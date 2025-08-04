(s:bodyshift.params)=
## BodyShiftP: Element Body Orientation and Position Parameters

Parameters describing where the physical element is with respect to its nominal position.
This parameters group can be used to simulate positional errors. See section [](#s:lab.body.transform)
for documentation on the body shift transformation.

The components of this group and their defaults are:
```{code} yaml
fork1:              # [string] user-defined name
  kind: BodyShiftP
  x_offset: 0       # [m] Offset along x-axis
  y_offset: 0       # [m] Offset along y-axis
  z_offset: 0       # [m] Offset along z-axis
  x_rot: 0          # [radian] Rotation around x-axis
  y_rot: 0          # [radian] Rotation around y-axis
  z_rot: 0          # [radian] Rotation around z-axis
```

