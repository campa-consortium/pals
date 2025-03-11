(c:element.parameters)=
# Element Parameters

Lattice elements parameters are organized into **parameter groups**. 
All groups are organized as abstract syntax trees.
At the top level, there are the groups with names like 
`MagneticMultipoleP`, `ElectricMultipoleP`, `MetaP`, `AlignmentP`, etc. 
By convention, group names use upper camel case and it is highly recommended that this convention
be followed but it is not mandatory. Also, by convention, parameter groups end with a `P`.
This is to distinguish between element types and parameter groups which might
have similar names. For example, `Fork` is the name of an element type and `ForkP`
is the name of a parameter group which a `Fork` element will have.

There are two element parameters that are so common that they are not grouped. 
These element parameters are `length` (element length) and `name` (name of element).

For any given element, a given parameter group can only appear once. For example,
the following is not allowed:
```{code} yaml
Quadrupole:
  name: q10w
  MetaP: ...
  MetaP: ...    # Second instance not allowed!
```

## Naming and Inheriting Parameters

Any group can be given a **name** and the values can be used in another group of the same type
using **import**.
For example:
```{code} yaml
ApertureP:
  name: ap1
  x_limit: [-0.03, 0.04]
```
The above defines an aperture with the name **ap1**. 
```{code} yaml
ApertureP:
  name: ap2
  inherit: ap1
  y_limit: [-0.02, 0.05]
```
And the above defines a new aperture group which inherits from **ap1**.

Naming a parameter group is only needed if the parameter group is defined outside of an element.
```{code} yaml
Element:
  name: q1
  ApertureP: 
    x_limit: [-0.03, 0.04]
    y_limit: [-0.02, 0.03]
```
And an element can inherit a parameter group from another element:
```{code} yaml
Element:
  name: q2
  ApertureP:
    inherit: q1.ApertureP
```

For an element to inherit all parameter groups from another element, just inherit the element itself:
```{code} yaml
Element:
  name: q3
  inherit: q2
```

%---------------------------------------------------------------------------------------------------
(s:ac.kicker.params)=
## ACKickerP:  AC-Kicker Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:aperture.params)=
## ApertureP: Aperture Parameters

The `ApertureP` parameter group contains parameters for describing an aperture. 
The components of this group are:
```{code} yaml
x_limit                      # [m] Vector of two real numbers
y_limit                      # [m] Vector of two real numbers
shape                        # Switch
location                     # Switch
aperture_shifts_with_body    # Boolian
vertices                     # Structure
material                     # String
thickness                    # [m] Real number
```

### Location component

The aperture location is set by the `location` parameter. Possible values are
```{code} yaml
ENTRANCE_END   # Body entrance end (default)
CENTER         # Element center
EXIT_END       # Body exit end
BOTH_ENDS      # Both ends
NOWHERE        # No location
EVERYWHERE     # Everywhere
```
The default is `ENTRANCE_END`.

### Shape component

```{figure} figures/apertures.svg
:width: 90%
:name: f:aperture

A) RECTANGULAR and ELLIPTICAL apertures. As drawn, `x_limit[1]` and `y_limit[1]` are 
negative and `x_limit[2]` and `y_limit[2]` are positive. B) The `vertices` aperture is defined
by a set of vertices.
```

The `shape` parameter selects the shape of the aperture. Possible values are:
```{code} yaml
RECTANGULAR   # Rectangular shape.
ELLIPTICAL    # Elliptical shape.
VERTICES      # Shape defined by set of vertices.
CUSTOM_SHAPE  # Shape defined outside of the lattice standard.
```

### x_limit and y_limit components

For `RECTANGULAR` and `ELLIPTICAL` shapes the `x_limit` and `y_limit` parameters are
used to calculate the aperture as shown in {numref}`f:aperture`A. 
For an `ELLIPTICAL` aperture, a particle with position {math}`(x, y)`
is outside of the aperture if any one of the following four conditions is true:
```{code}
  1) x < 0 and y < 0 and (x/x_limit[1])^2 + (y/y_limit[1])^2 > 1 
  2) x < 0 and y > 0 and (x/x_limit[1])^2 + (y/y_limit[2])^2 > 1
  3) x > 0 and y < 0 and (x/x_limit[2])^2 + (y/y_limit[1])^2 > 1
  4) x > 0 and y > 0 and (x/x_limit[2])^2 + (y/y_limit[2])^2 > 1
```
For a `RECTANGULAR` aperture the corresponding four conditions are:
```{code}
  1) x < x_limit[1]
  2) x > x_limit[2]
  3) y < y_limit[1]
  4) y > y_limit[2]
```

Default values for the limits are `[-Inf, Inf]` for both `x_limit` and `y_limit`.

### misalignment_moves_aperture

The `misalignment_moves_aperture` parameter determines whether misaligning an element 
affects the placement of the aperture. The default is `False`. 
A common case where `misalignment_moves_aperture` would be `False` is when a beam pipe,
which incorporates the aperture, is not physically touching the surrounding magnet element. 
When tracking a particle, assuming that there are only apertures at the element ends, 
the order of computation with `misalignment_moves_aperture` set to `False` could be
```{code} yaml
  1) Start at upstream end of element
  2) Check upstream aperture if there is one.
  3) Convert from branch coordinates to body coordinates.
  4) Track through the element body.
  5) Convert from body coordinates to branch coordinates.
  6) Check downstream aperture if there is one.
  7) End at downstream end of element.
```
With `misalignment_moves_aperture` set to `True`, the computation order could be
```{code} YAML
  1) Start at upstream end of element
  2) Convert from branch coordinates to body coordinates.
  3) Check upstream aperture if there is one.
  4) Track through the element body.
  5) Check downstream aperture if there is one.
  6) Convert from body coordinates to branch coordinates.
  7) End at downstream end of element.
```

### material

The `material` parameter sets the material of the aperture. 
Using chemical formulas like `Cu` and `Fe` are the most portable.

### vertices component

The `VERTICES` setting for `shape` is for defining an aperture using a 
set of vertex points as illustrated in {numref}`f:aperture`B. 
Between vertex points, the aperture can can follow a straight line or the arc of an ellipse. 
The vertex points are specified by setting the `vertices` parameter. This parameter has three
subcomponents
```{code} yaml
center              # [m] Vector of [x, y] center point.
absolute_vertices   # Boolian. Default is False.
list                # Struct. Ordered list of vertex points.
```
The `list` vector can have the components:
```{code} yaml
point       # [m] Vector of two real numbers.
radius      # [m] Vector of single or two real numbers.
tilt        # [rad/2pi] Ellipse tilt angle.
```
Example:
```{code} yaml
ApertureP:
  vertices:
    center: [-0.045, 0.011]
    absolute_vertices: True
    list:
      - point: [0.023, 0.069]      # V1
      - point: [-0.025, 0.067]     # V2
      - radius: [0.08, 0.04]
      - tilt: 0.12
      - point: [-0.088, 0.036]     # V3
      - point: [-0.088, -0.021]    # V4
      - point: [0.023, -0.033]     # V5
```
This corresponds roughly to what is shown in {numref}`f:aperture`.

If the boolean `absolute_vertices` is set `False`, which is the default,
the vertex point positions are with respect to the `center` point. 
That is, the vertex point positions in absolute terms are the positions given with each vertex plus
the position of the `center`. If `absolute_vertices` is `True`, the vertex point positions 
are independent of the `center` point. The default position of the `center` is the origin.

The `list` component of `vertices` contains an ordered  list of vertex 
`point`s with each one specifying an {math}`(x, y)` position. 
In between any two `point`s, there can optionally be a single `radius` element.
If there is a `radius` element, there can also be a  single `tilt` element between
the `point`s but `tilt` can only be present if there is a `radius` present.
There can also be a `radius` element and `tilt` element after the last `point` in the `list`. 
If these are present, they are considered to be between the last and fist `point`s in the list.

The aperture is constructed by connecting consecutive `point`s in the `list` along with
connecting the last `point` to the first. If there is no `radius` between consecutive `point`s,
the aperture follows a straight line between the points. If there is a `radius` element between
two points, the aperture is either a circular arc or a section of an ellipse. 
A `radius` can have either a single value or a list of two values. If a `radius` has a single
value, this is the radius of the circular arc connecting the vertices. In this case, the `tilt`
element may not be present. If the `radius` has two values, these are the half lengths of the 
principal diameters. If the `tilt` is zero (the default), the ellipse is upright with the first 
`radius` value being the {math}`x`-axis half width and the second value being the {math}`y`-axis
half width. A non-zero `tilt` value rotates the ellipse by that amount. 

In order to be able to quickly calculate whether a particle is inside or outside the
aperture, the aperture shape has some restrictions. For one, 
the vertex points must be arranged so that the polar coordinate angle of the vertex points
with respect to the `center` point is increasing. That is, for vertices {math}`v_i` and
{math}`v_{i+1}` that are at angles {math}`\theta_i` and {math}`\theta_{i+1}` with respect
to the `center` point:
```{math}
  0 < \theta_{i+1} - \theta_{i} \pmod{2\pi} < \pi
```
Another restriction is that any half-line drawn from the `center` point out to infinity intersects
the aperture at exactly one point. Finally, for a circular or elliptical arc, of
the four possible solutions that connect the two vertex points at the ends of the arc, 
the arc used is the arc of minimal length such that the center of the ellipse is on the same side
as the `center` point with respect to a line drawn through the two points.

When using vertices, an efficient way to determine if a point {math}`(x, y)` is within the aperture
is the following. Note: The computation is with respect to the `center` point.
```{code} yaml
  0) Determine the polar coordinate angles {math}`\theta_i` of the vertices. These angles can be 
stored so this computation only has to be done once.
  1) Determine the angle of the particle.
  2) A simple binary search will give the neighboring pair of vertices the particle's angle falls between.
  3) A simple geometric calculation now determines where the half line drawn from the `center`
and through the particle point intersects the aperture.
  4) The particle is outside the aperture if and only if the intersection point is between the 
particle point and the `center` point.
```

%---------------------------------------------------------------------------------------------------
(s:beambeam.params)=
## BeamBeamP: Beambeam Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:bend.params)=
## BendP: Bend Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:elecmult.params)=
## ElectricMultipoleP:  Electric Multipole Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:floor.params)=
## FloorP: Floor Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:fork.params)=
## ForkP: Parameters

The `ForkP` parameter group holds parameters for a `Fork` element.
The components of this group are:
```{code} yaml
  to_line               # String: Beam line to fork to
  to_ele                # String: Element forked to.
  direction             # Switch: Longitudinal Direction of travel of injected beam.
  propagate_reference   # Boolian: Propagate reference species and energy?
```
The possible values of the optional `direction` switch are:
```{code} yaml
FORWARDS            # Injected particle propagates in forward direction. Default.
BACKWARDS           # Injected particle propagates in reverse direction.
```

See the [](#s:forking) chapter for more details.

%---------------------------------------------------------------------------------------------------
(s:girder.params)=
## GirderP: Girder Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:init.particle.params)=
## InitialParticleP: Initial Particle Coordinates Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:mag.mult.params)=
## MagneticMultipoleP: Magnetic Multipole Parameters

The `MagneticMultipoleP` parameter group describes magnetic multipoles associated with the lattice
element. For a multipole of order `N`, the magnetic field {math}`(B_x, B_y)`
at a point {math}`\bf r` in terms of the points polar coordinates {math}`(r, \theta)` is
```{math}
:label: bbmult

B_x({\bf r}) + i \, B_y({\bf r}) = 
\frac{1}{N!}(B_n + i \, B_s) \, e^{-i(N+1)T} \, e^{iN\theta} \, r^N
```
where {math}`T` is the "tilt" of the `N`{sup}`th` multipole and {Math}`B_n` and {math}`B_s` are
the normal and skew components of the field. `N` is defined such that 
{math}`N = 0` describes a dipolar multipole, {math}`N = 1` describes a quadrupolar multipole, etc.

The three parameters, {math}`T`, {Math}`B_n` and {math}`B_s` are not independent and only two
are needed to specify a multipole. 
However, it is sometimes convenient to use all three. 
For example, {Math}`B_n` and {math}`B_s` with {math}`N=0` can be used to describe 
an element with independent horizontal and vertical steerings while {math}`T` can be used
to represent rotational errors.

The components of `MagneticMultipoleP` for specifying a multipolar field of order `N` is:
```{code} yaml
tiltN     - Tilt
BnN       - Normal component 
BsN       - Skew component
```

Alternatively, the field components can be specified using normalized values
```{code} yaml
KnN       - Normalized normal component 
KsN       - Normalized skew component
```
where the conversion between field and normalized components is:
```{math}
  (K_n, K_s) = \frac{q}{P_0} \, (B_n, B_s)
```
with {math}`q` being the charge of the reference particle and {math}`P_0` being the 
reference momentum.

Furthermore, the field and normalized values can be given in terms of the integrated strength.
Integrated values are specified with the letter 
`L` appended at the end of the name. Example:
```{code} yaml
MagneticMultipoleP:
  tilt7: 0.7        - Tilt of 7th order multiple
  Bn3: 27.3         - Normal multipole component of order 3.
  Bn3L: 3.47e1      - Length integrated normal multipole component of order 3.
```
The length integrated values are related to the non-integrated values via
```{math}
  (B_n, B_s, K_n, K_s) = L \, (B_n, B_s, K_n, K_s)
```
where `L` is the length of the element.

For a given element, when specifying a multipole of a given order, 
the two strength components must be of the same type.
That is, it is not permitted for one component to be length integrated and the other not,
as well as it is not permitted for one component to be a field and the other component to be normalized.
However, the multipole components of different order do not have to be of the same type.

When multipoles are specified for a `Bend` element, the calculation of the field is
complicated by the curvilinear coordinate system.
The `geometry` component switch can be used to specify how to calculate the multipole fields. 
Possible settings for this component are:
```{code} yaml
vertically_pure
horizontally_pure
entrance_tangent
exit_tangent
chord_tangent
```
The `entrance_tangent` setting is used when the [reference curve](#s:coords) for the 
multipole coordinate system is the straight line tangent to the entrance coordinates of the bend. 
Similarly, the `exit_tangent` setting is used when the reference curve is the 
straight line tangent to the exit coordinates of the bend. And the `chord_tangent` setting is used
when the reference curve is the straight line connecting the entrance point to the
exit point. In all these three cases, since the multipole reference curve is a straight line, 
Eq. [](#bbmult) is valid.
Note that for these cases, the multipole reference curve 
is not the same as the [`branch` reference curve](#s:coords).

If `geometry` is set to `vertically_pure` or `horizontally_pure`, the reference curve
for the multipoles is the circular arc of the bend corresponding to the `branch` reference curve. 
This is discussed in detail in [](#c:multipole.bend).

%---------------------------------------------------------------------------------------------------
(s:meta.params)=
## MetaP: Metadata Parameters

The `MetaP` parameter group can be used for metadata that describes the lattice element
but is not part of the PALS standard. Such data is necessarily program dependent.
Example metadata could be blueprint information, information on power supply connections, etc.
Example:
```{code} yaml
MetaP:
  alias:  an_alternative_name
  Meta: Mark 4 quadrupole
```

Components of `MetaP` are not limited to being simple strings or numbers but can be complex 
structures. The information contained in `MetaP` should be restricted to information that 
does not affect simulations. Custom, program specific information should be stored elsewhere.

%---------------------------------------------------------------------------------------------------
(s:patch.params)=
## PatchP:  Patch Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:reference.params)=
## ReferenceP: Reference Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:rf.params)=
## RFP: RF Parameters

In Construction...

%---------------------------------------------------------------------------------------------------
(s:solenoid.params)=
## SolenoidP: Solenoid Parameters

In Construction...

