(s:floor.shift.params)=
## FloorShiftP:  FloorShift Parameters

The `FloorShiftP` parameter group describes the shift the reference curve of a `FloorShift` element.
The components of `FloorShiftP` are:
```{code} yaml
  x_offset
  y_offset
  z_offset
  t_offset
  
  x_rot
  y_rot
  z_rot
```

Example:
```{code} yaml
FloorShiftP:
  x_offset:  0.34
  z_offset: 1.7
  z_rot: 0.23
```