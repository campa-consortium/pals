%---------------------------------------------------------------------------------------------------
(s:tracking.params)=
## TrackingP: Parameters Pertaining to Tracking.

Tracking parameters are highly program specific but it is useful to have a group
having some standardization.

The `TrackingP` parameter group contains parameters for describing the particle
tracking.
The components of this group are:
```{code} yaml
ReferenceP:
  tracking_type: "" # [string] type of tracking
  start_loc: ""     # [string] Where tracking starts
  end_loc: ""       # [string] Where tracking ends
  ...
```
In Construction...

