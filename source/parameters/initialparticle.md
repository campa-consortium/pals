%---------------------------------------------------------------------------------------------------
(s:init.particle.params)=
## InitialParticleP: Initial Particle Coordinates Parameters

The `InitialParticleP` parameter group contains parameters for describing the 
initial beam particle distribution.
The components of this group are:
```{code} yaml
InitialParticleP:
  distribution_type: ""    # [string] name of initial distribution type
  sigma_x: null            # RMS x = sqrt(<x^2>)
  sigma_px: null           # RMS px = sqrt(<px^2>)
  mu_xpx: null             # <xpx>/(sigma_x*sigma_px) where <> denotes average over distribution
  x_off: null              # <x>
  px_off: null             # <px>
  sigma_y: null            # RMS y = sqrt(<y^2>)
  sigma_py: null           # RMS py = sqrt(<py^2>)
  y_off: null              # <y>
  py_off: null             # <py>
  mu_ypy: null             # <ypy>/(sigma_y*sigma_py)
  sigma_z: null            # RMS z = sqrt(<z^2>)
  sigma_pz: null           # RMS pz = sqrt(<pz^2>)
  mu_zpz: null             # <zpz>/(sigma_z*sigma_pz)
  z_off: null              # <z>
  pz_off: null             # <pz>
```

