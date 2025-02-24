# Definitions

- `Branch`: Essentially an ordered list of lattice elements that can be tracked through.
A branch can describe such things as a storage ring or Linac.
- `Branch expansion`: The process, starting from the `root` `BeamLine`
of a branch, of constructing the ordered list of lattice elements contained in that branch.
- `Element`: See `Lattice element`.
- `Latttice`: The outermost structure that essentially holds a set of branches and
can be used to define an entire accelerator complex.
- `Lattice expansion`: This includes `branch expansion` along with connecting branches
together via `Fork` elements, expression evaluations, 
and floor position and reference species and energy calculation. 
- `Root BeamLine`: A `BeamLine` that is used as the basis for creating a branch.
- `Root branch`: A branch that is specified in a `Lattice` structure. Non-root branches
are branches that are formed due to the presence of `Fork` elements.
- `Lattice element`: Basic building block of a lattice most often representing something
physical like a quadrupole magnet or an RF cavity.
