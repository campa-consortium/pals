%---------------------------------------------------------------------------------------------------
(s:init.particle.params)=
## InitialParticleP: Initial Particle Coordinates Parameters

The `InitialParticleP` parameter group contains parameters for describing the 
initial beam particle distribution.
The components of this group are:
```{code} yaml
InitialParticleP:
  Distype: ""    # [string] name of initial distribution type
  sigx           # RMS x = sqrt(<x^2>)
  sigpx          # RMS px = sqrt(<px^2>)
  muxpx          # <xpx>
  xoff           # <x>
  pxoff          # <px>
  sigy           # RMS y = sqrt(<y^2>)
  sigpy          # RMS py = sqrt(<py^2>)
  yoff           # <y>
  pyoff          # <py>
  muypy          # <ypy>
  sigz           # RMS z = sqrt(<z^2>)
  sigpz          # RMS pz = sqrt(<pz^2>)
  muzpz          # <zpz>
  zoff           # <z>
  pzoff          # <pz>
```

