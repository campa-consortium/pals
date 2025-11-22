%---------------------------------------------------------------------------------------------------
(s:init.particle.params)=
## InitialParticleP: Initial Particle Coordinates Parameters

The `InitialParticleP` parameter group contains parameters for describing the 
initial beam particle distribution based on its first two moments.
The components of this group are:
```{code} yaml
InitialParticleP:
  distribution_type: ""  # [string] name of initial distribution type
  x_off:    null         # <x>, <> denotes average over distribution
  px_off:   null         # <px>
  y_off:    null         # <y>
  py_off:   null         # <py>
  z_off:    null         # <z>
  pz_off:   null         # <pz>
  sigma_x:  null         # RMS x = sqrt(<x^2>)
  sigma_px: null         # RMS px = sqrt(<px^2>)
  sigma_y:  null         # RMS y = sqrt(<y^2>)
  sigma_py: null         # RMS py = sqrt(<py^2>)
  sigma_z:  null         # RMS z = sqrt(<z^2>)
  sigma_pz: null         # RMS pz = sqrt(<pz^2>)
  mu_xpx:   null         # <xpx> 
  mu_xy:    null         # <xy> 
  mu_xpy:   null         # <xpy> 
  mu_xz:    null         # <xz> 
  mu_xpz:   null         # <xpz> 
  mu_pxy:   null         # <pxy> 
  mu_pxpy:  null         # <pxpy> 
  mu_pxz:   null         # <pxz> 
  mu_pxpz:  null         # <pxpz> 
  mu_ypy:   null         # <ypy>
  mu_yz:    null         # <yz>
  mu_ypz:   null         # <ypz>
  mu_pyz:   null         # <pyz>
  mu_pypz:  null         # <pypz>
  mu_zpz:   null         # <zpz>
```

