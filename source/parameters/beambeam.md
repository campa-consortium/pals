(s:beambeam.params)=
## BeamBeamP: BeamBeam Parameters

The `BeamBeamP` parameter group describes a particle beam element
from the opposite moving colliding beam. 

The inputs of `BeamBeamP` are:
```{code} yaml
BeamBeamP:
  sigma_x      # The horizontal beam size of the opposite beam (default: 1 mm).
  sigma_y      # The vertical beam size of the opposite beam (default: 1 mm).
  sigma_z      # The longitudinal beam size of the opposite beam (default: 0 m).
  alpha_x   # The horizontal Twiss parameter alpha at interaction point (default: 0).
  beta_x    # The horizontal Twiss parameter beta at interaction point (default 1 m).
  alpha_y   # The vertical Twiss parameter alpha at interaction point (default 0 m).
  beta_y    # The vertical Twiss parameter beta at interaction point (default 1 m).
  charge    # The charge of the opposite beam (default: 1 for proton).
  energy    # The total energy in eV of the opposite beam (default: 1e12.
  N_particle  # Number of particles in the opposite beam (default: 0).
```

