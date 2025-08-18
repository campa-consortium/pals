%---------------------------------------------------------------------------------------------------
(s:rf.params)=
## RFP: RF Parameters

The components of this group and their defaults are:
```{code} yaml
sol1:                           # [string] user-defined name
  kind: Solenoid
  frequency: 0                  # [Hz] RF frequency
  harmon: 0                     # [unitless] RF frequency harmonic number
  voltage: 0                    # [V] RF voltage
  gradient: 0                   # [V/m] RF gradient
  phase: 0                      # [unitless] RF phase in 0 to 2*pi
  multipass_phase: 0            # [unitless] RF Phase added to multipass elements
  cavity_type: STANDING_WAVE    # [string] Cavity type
  n_cell: 1                     # [unitles] Number of cavity cells
```

Whether `voltage` or `gradient` is kept constant with length changes is determined by
the setting of `field_master` ([](#s:master.g)). If `field_master` is `true`, the
`gradient` is kept constant and vice versa.
