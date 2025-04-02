%---------------------------------------------------------------------------------------------------
(s:bend.params)=
## BendP: Bend Parameters

The `BendP` group stores the parameters that characterize the shape of a [`Bend`](#s:bend) element. 
The only relevant shape parameter that is not in the `BendP` is the
length `Length` parameter.

The parameters of this group are:
```{code} yaml
angle             - Reference bend angle.
bend_field_ref    - Reference bend field.
bend_type         - Type of bend. Default: SECTOR.
e1                - Entrance end pole face rotation.
e2                - Exit end pole face rotation.
e1_rect           - Entrance end pole face rotation.
e2_rect           - Exit end pole face rotation.
edge_int1         - Entrance end fringe field integral.
edge_int2         - Exit end fringe field integral
g                 - Reference bend strength = 1/radius.
h1                - Entrance end pole face curvature.
h2                - Exit end pole face curvature.
L_chord           - Chord length.
tilt_ref          - Reference tilt.
```

```{figure} figures/bend.svg
:name: f:bend
:width: 90%
 
Bend geometry. Red dots are the entry and exit points that define the origin for the
coordinate systems at the entry end {math}`(s_1, x_1)` and exit ends {math}`(s_2, x_2)` respectively.

A) Bend geometry with positive bend angle. For the geometry shown,
`g`, `angle`, `rho`, `e1`, `e2`, `e1_rect`, and `e2_rect` are all positive.

B) Bend geometry with negative bend angle. For the geometry shown,
`g`, `angle`, `rho`, `e1`, `e2` are all negative.
Note: The figures are drawn for zero `tilt_ref` where the rotation axis is parallel to the
{math}`y`-axis.
```

In detail:
- **angle**
The total Reference bend angle. A positive `angle` represents a
bend towards negative {math}`x` as shown in {numref}`f:bend`.
%
- **bend_field_ref**
The `bend_field_ref` parameter is the reference magnetic bending field which is the field
that is needed for the reference particle to be bent in a circle of radius `rho`
and the placement of lattice elements downstream from the bend. The actual ("total") field is
a vector sum of
`bend_field_ref` plus the value of the `Bn0`  and `Bs0` multipoles. If `tilt0` and `Bs0`
are zero, the actual field is
  ```{code} yaml
  B-field(total) = bend_field_ref + Bn0
  ```
  See the discussion of `g` and `Kn0` below for more details.
%
- **bend_field (output param), norm_bend_field (output_param)**
The actual dipole bend field ignoring any skew field component which is set by `Bs0`.
The relation between this and `bend_field_ref` is
  ```{code} yaml
  bend_field = bend_field_ref + Bn0 * cos(tilt0) + Bs0 * sin(tilt0)
  ```
%
- **bend_type**
The `bend_type` parameter sets the "logical shape" of the bend.
This parameter can take values of
  ```{code} yaml
  RECTANGULAR  - or
  SECTOR       - the default
  ```
  The logical shape of a bend, in most situations, is irrelevant.
  The only case where the logical shape is used is when the bend angle is varied.
  In this case, for a `SECTOR` bend, the face angles `e1` and `e2` are
  held constant and `e1_rect` and `e2_rect` are varied to keep the relationship
  between `e1` and `e1_rect`, and `e2` and `e2_rect` satisfied as discussed below.
%
- **e1, e2**
The values of `e1` and `e2` gives the rotation angle of the entrance and exit pole faces
respectively with respect to the radial {math}`x_1` and {math}`x_2` axes as shown in {numref}`f:bend`.
Zero `e1` and `e2` gives a wedge shaped magnet.
Also see `e1_rect` and `e2_rect`. The relationship is
  ```{code} python
  :label: eeaeea

  e1 = e1_rect + angle/2 
  e2 = e2_rect + angle/2
  ```
%
- **e1_rect, e2_rect**
Face angle rotations like `e1` and `e2` except angles are measured with respect to
fiducial lines that are parallel to each other and rotated by `angle`/2 from the radial
{math}`x_1` and {math}`x_2` axes as shown in {numref}`f:sbend`.
Zero `e1_rect` and `e2_rect` gives a rectangular magnet shape.
%
- **edge_int1, edge_int2**
The field integral for the entrance pole face `edge_int1` is given by
  ```{math}
  \text{edge_int1} = \int_{pole} \!\! ds \frac{B_y(s) (B_{y0} - B_y(s))}
  {2 , B_{y0}^2}
  ```
  For the exit pole face there is a similar equation for `edge_int2`

  Note: In Bmad and MAD, these integrals are represented by the product of `fint` and `hgap`.

  `edge_int1` and `edge_int2` can be related to the Enge function which is sometimes used to model the
  fringe field. The Enge function is of the form
  ```{math}
  B_y(s) = \frac{B_{y0}}{1 + \exp[P(s)]}
  ```
  ```{math}
  P(s) = C_0 + C_1 , s + C_2 , s^2 + C_3 , s^3 + , \ldots
  ```
  The {math}`C_0` term simply shifts where the edge of the bend is. If all the {math}`C_n` are zero except for
  {math}`C_0` and {math}`C_1` then
  ```{math}
  C_1 = \frac{1}{2 \cdot \text{field_int}}
  ```
%
- **g, rho (output param)**
The Reference bending radius which determines the reference coordinate system is `rho` (see
[](#s:ref)). `g` = `1/rho` is the "bend strength" and is proportional to the Reference
dipole magnetic field. `g` is related to the reference magnetic field `bend_field_ref` via
  ```{math}
  :label: gqpb

  \text{g} = \frac{q}{p_0} \cdot \text{bend_field_ref}
  ```
where {math}`q` is the charge of the reference particle and {math}`p_0` is the reference momentum. It is
important to keep in mind that changing `g` will change the Reference orbit ([](#s:coords.3)) and
hence will move all downstream lattice elements in space.

  The total bend strength felt by a particle is the vector sum of `g` plus the zeroth order
magnetic multipole. If the multipole `tilt0` and `Ks0` is zero, the total bend strength is
  ```{code} yaml
  norm_bend_field = g + Kn0
  ```
  Changing the multipole strength `Kn0` or `Ks0` leaves the Reference orbit and the positions of
all downstream lattice elements
unchanged but will vary a particle's orbit. One common mistake when designing lattices is to vary
`g` and not `Kn0` which results in downstream elements moving around. See Sref{s:ex.chicane}
for an example.

  Note: A positive `g`, which will bend particles and the reference orbit in the {math}`-x` direction
represents a field of opposite sign as the field due a positive `hkick`.
%
- **h1, h2**
The attributes `h1` and `h2` are the curvature of the entrance and exit pole faces.
%
- **L, L_arc, L_chord, L_sagitta (output param)** 
The `Length` parameter, is the arc length of the reference trajectory through the bend.

  `L_chord` is the chord length from entrance point to exit point.
The `L_sagitta` parameter is the sagitta length (The sagitta is the distance
from the midpoint of the arc to the midpoint of the chord). `L_sagitta` can be negative and will have
the same sign as the `g` parameter.
%
- **L_rectangle**
The `L_rectangle` parameter is the "rectangular" length defined to be the distance between the
entrance and exit points. The coordinate system used for the calculation is defined by the setting
of `fiducial_pt`. {numref}`f:rbend` shows `l_rectangle` for `fiducial_pt` set to
`entrance_end` (the coordinate system corresponds to the entrance coordinate system of the bend).
In this case, and in the case where `fiducial_pt` is set to `exit_end`, the rectangular
length will be {math}`rho sinalpha`. If `fiducial_pt` is set to `none` or `center`,
`l_rectangle` is the same as the chord length.
%
- **tilt_ref**
The `tilt_ref` attribute rotates a bend about the longitudinal axis at the entrance face of the
bend. A bend with `tilt_ref` of {math}`\pi/2` and positive `g` bends the element in the {math}`-y`
direction ("downward"). See {numref}`f:tilt.bend`. It is important to understand that `tilt_ref`,
unlike the `tilt` attribute of other elements, bends both the reference orbit along with the
physical element. Note that the MAD `tilt` attribute for bends is equivalent to the Bmad
`tilt_ref`. Bends in Bmad do not have a `tilt` attribute.

  Important! Do not use `tilt_ref` when doing misalignment studies for a machine. Trying to misalign
a dipole by setting `tilt_ref` will affect the positions of all downstream elements! Rather, use the
`tilt` parameter.

%---------------

  The attributes `g`, `angle`, and `Length` are mutually dependent. If any two are specified for
an element, the lattice expansion code will calculate the appropriate value for the third.

  In the local coordinate system ([](#s:ref)), looking from "above" (bend viewed from positive
{math}`y`), and with `tilt_ref` = 0, a positive `angle` represents a particle rotating clockwise. In
this case. `g` will also be positive. For counterclockwise rotation, both `angle` and `g`
will be negative but the length `Length` is always positive. Also, looking from above, a positive
`e1` represents a clockwise rotation of the entrance face and a positive `e2` represents a
counterclockwise rotation of the exit face. This is true independent of the sign of `angle` and
`g`. Also it is always the case that the pole faces will be parallel when
  ```{code} yaml
  e1 + e2 = angle
  ```
