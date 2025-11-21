(s:beambeam.params)=
## BeamBeamP: BeamBeam Parameters

The `BeamBeamP` parameter group describes a particle beam element
from the opposite moving colliding beam. 

The inputs of `BeamBeamP` are:
```{code} yaml
BeamBeamP:
  sigma_x: 0.001    # The horizontal beam size of the opposite beam (default: 1 mm).
  sigma_y: 0.001    # The vertical beam size of the opposite beam (default: 1 mm).
  sigma_z: 0.0      # The longitudinal beam size of the opposite beam (default: 0 m).
  alpha_x: 0.0   # The horizontal Twiss parameter alpha at interaction point (default: 0).
  beta_x: 1.0    # The horizontal Twiss parameter beta at interaction point (default 1 m).
  alpha_y: 0.0   # The vertical Twiss parameter alpha at interaction point (default 0 m).
  beta_y: 1.0    # The vertical Twiss parameter beta at interaction point (default 1 m).
  charge: 1.0    # The charge of the opposite beam (default: 1 for proton).
  energy: 1e12    # The total energy in eV of the opposite beam (default: 1e12.
  N_particle: 0.0  # Number of particles in the opposite beam (default: 0).
```

