(s:beambeam.params)=
## BeamBeamP: BeamBeam Parameters

The `BeamBeamP` parameter group describes a particle beam element
from the opposite moving colliding beam. 

The inputs of `BeamBeamP` are:
```{code} yaml
BeamBeamP:
  sigx      # The horizontal beam size of the opposite beam (default: 0 m).
  sigy      # The vertical beam size of the opposite beam (default: 0 m).
  sigz      # The longitudinal beam size of the opposite beam (default: 0 m).
  alpha_x   # The horizontal Twiss parameter alpha at interaction point
  beta_x    # The horizontal Twiss parameter beta at interaction point
  alpha_y   # The vertical Twiss parameter alpha at interaction point
  beta_y    # The vertical Twiss parameter beta at interaction point
  charge    # The charge of the opposite beam (default: 1 for proton).
  energy    # The total energy in eV of the opposite beam.
  Npart     # Number of charged particles of the opposite beam.
```

