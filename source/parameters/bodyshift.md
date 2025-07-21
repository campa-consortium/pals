(s:bodyshift.params)=
## BodyShiftP: Element Body Orientation and Position Parameters

Parameters describing where the physical element is with respect to its nominal position.
This parameters group can be used to simulate positional errors. See section [](#s:lab.body.transform)
for documentation on the body shift transformation.

The parameters of this group are:
```{code} yaml
  x_offset    # Offset along x-axis.
  y_offset    # Offset along y-axis.
  z_offset    # Offset along z-axis.
  x_rot       # Rotation around x-axis.
  y_rot       # Rotation around y-axis.
  z_rot       # Rotation around z-axis.
```

