%---------------------------------------------------------------------------------------------------
(s:rf.params)=
## RFP: RF Parameters

The components of this group are:
```{code} yaml
frequency         - RF frequency.
harmon            - RF frequency harmonic number.
voltage           - RF voltage.
gradient          - RF gradient.
phase             - RF phase.
multipass_phase   - RF Phase added to multipass elements.
cavity_type       - Cavity type. Default is STANDING_WAVE.
n_cell            - Number of cavity cells. Default is 1.
```

Whether `voltage` or `gradient` is kept constant with length changes is determined by
the setting of `field_master` ([](#s:master.g)). If `field_master` is `true`, the
`gradient` is kept constant and vice versa.
