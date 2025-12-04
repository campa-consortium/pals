(s:beambeam.params)=
## BeamBeamP: BeamBeam Parameters

The `BeamBeamP` parameter group describes a particle beam element
from the opposite moving colliding beam. 

The inputs of `BeamBeamP` are:
```{code} yaml
BeamBeamP:
  sigma_x: 0.001    # [m] The horizontal beam size of the opposite beam with default value of 1 mm.
  sigma_y: 0.001    # [m] The vertical beam size of the opposite beam with default value of 1 mm.
  sigma_z: 0.0      # [m] The longitudinal beam size of the opposite beam with default value of 0 m.
  alpha_x: 0.0   # [unitless] The horizontal Twiss parameter alpha at interaction point with default value of 0.
  beta_x: 1.0    # [m] The horizontal Twiss parameter beta at interaction point with default value of 1 m.
  alpha_y: 0.0   # [unitless] The vertical Twiss parameter alpha at interaction point default value of 0 m.
  beta_y: 1.0    # [m] The vertical Twiss parameter beta at interaction point with default value of 1 m.
  charge: 1.0    # [unitless] The charge of the opposite beam with default value of 1 for proton.
  energy: 1e12    # [eV] The total energy in eV of the opposite beam with default value of 1e12.
  N_particle: 0.0  # [unitless] Number of particles in the opposite beam with default value of 0.
```

