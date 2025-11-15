(s:beambeam.params)=
## BeamBeamP: BeamBeam Parameters

The `BeamBeamP` parameter group describes a particle beam element
from the opposite moving colliding beam. 

The inputs of `BeamBeamP` are:
```{code} yaml
BeamBeamP:
  sigx      # The horizontal beam size of the opposite beam (default: 0 m).
  sigy      # The vertical beam size of the opposite beam (default: 0 m).
  xdisp     # The horizontal displacement of the opposite beam (default: 0 m).
  ydisp     # The vertical displacement of the opposite beam (default: 0 m).
  charge    # The charge of the opposite beam (default: 1 for proton).
  energy    # The total energy in eV of the opposite beam.
  Npart     # Number of charged particles of the opposite beam.
```

