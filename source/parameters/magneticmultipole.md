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
```{code} yaml
  (BnL, BsL, KnL, KsL) = L * (Bn, Bs, Kn, Ks)
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

