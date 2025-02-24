(c:lattice-construct)=
# Lattice Construction

%---------------------------------------------------------------------------------------------------
(s:lattice.construct)=
## Constructing a Lattice

A `Lattice` is essentially a set of branches. 
Each branch is instantiated from a `BeamLine` which is called the a `root BeamLine`.
Example:
```{code} yaml
Lattice:
  - Branch: this_line    # Root beamline.
  - Branch:
      name: some_name
      BeamLine: that_ring
      periodic: True
```
In this example, `this_line` and `that_ring` are the names of the root BeamLines
for the two `Branches` that will be created when the lattice is [expanded](#s:expansion).
Branches created due to `Fork` elements also have root `BeamLines`. `Branches` specified
in the `Lattice` structure are called `root branches` of the `lattice`. Non-root branches
are those branches created due to `Fork` elements.

A `Branch` has the optional components
```{code} yaml
name      # Optional String. Name of the branch. Default is the name of the root BeamLine.
periodic  # Optional Bool. Are orbit and Twiss parameters periodic? 
          #   Default is the setting of the root BeamLine.
```
The setting of `periodic` or `name` for a `Branch` overrides the setting of `periodic` or `name`
set in the root `BeamLine`. See [](#s:beamline.components) for documentation of `periodic`.

%---------------------------------------------------------------------------------------------------
(s:branch.expand)=
## Branch Expansion

`Branch expansion` is the process, starting from the `root BeamLine`
of a branch, of constructing the ordered list of lattice elements contained in that branch.

The first lattice element of any root `BeamLine` line must be a `Beginning` element and the expanded
branch line may only contain this one `Beginning` element. If a subline contains a `Beginning`
element, this element must be dropped from the branch line.

The last lattice element of a branch line be a `Marker` element.

Notes:
- When a lattice is expanded, 
in any region of a `Branch` where the elements are not directionally reversed, the elements
must be ordered such that the longitudinal positions at the upstream end of the elements is ordered
in increasing {math}`s`-position value. For a region where the elements are directionally
reversed, the downstream end of the elements must be ordered in increasing {math}`s`-position.
This mandate on element ordering ensures that the order of elements in a directionally reversed
`BeamLine` is always the reverse of the order of elements in the non-reversed `BeamLine`.

%---------------------------------------------------------------------------------------------------
(s:lattice.expand)=
## Lattice Expansion

`Lattice expansion` is the process, starting from a `Lattice` structure instance, where:
- The `root BeamLines` of the branches are expanded.
- `Fork` elements in the Branches are used to construct new branches and, if these new branches
have `Fork` elements, this process is repeated until no new branches need to be created.
- The floor position along with the reference energy, species and time, of all the lattice elements 
is computed.
- Mathematical expressions are evaluated.

Notes:
- All branches must have unique names. However, different branches may use the same root `BeamLine`.
- As detailed in [](#s:forking), some `Fork` elements may connect to an existing branch.
These `Fork` elements will not trigger new branch creation. 
- The PALS standard does not mandate how branches should be stored in memory after expansion.
For example, branches could be stored using an array or a tree. 
In any case, the root branches must be marked as such.
- The order in which new branches are added to the lattice due to the presence of `Fork` elements 
is not mandated by PALS. This can lead to the situation where connecting a `Fork` element to 
what is designated as an existing branch is not possible since the branch being forked to 
does not yet exist since
the `Fork` element that instantiates this branch has not been processed yet. In this case,
the first `Fork` element must be temporarily ignored until the branch is instantiated.

%---------------------------------------------------------------------------------------------------
(s:forking)=
## Forking

A `Fork` element marks a point in a lattice branch where another branch is attached to. 
A common example is using a `Fork` element to connect from a storage ring to 
an extraction line or an X-ray beam line. Similarly, a `Fork` can be used to connect 
from the end of an injection line to someplace in a ring. 
An example of how forking can be used to construct complex machine layouts
is shown in figure {numref}`f:fork`. 

```{figure} figures/fork.svg
:width: 80%
:name: f:fork

Example of how `Fork` and `Patch` elements can be used to describe even complicated machine geometries. 
Shown is a section of the 8-pass (4 passes with increasing energy and 4 passes with decreasing energy) 
Cornell/Brookhaven CBETA ERL/FFAG machine. `Fork` elements are used to connect the 
injection line to the ERL and to connect the ERL to a diagnostic line. The geometry of the
switchyard, used to correct the timings of the beams with differing energies from the FFAG arc, 
is done using `Patch` elements.
```

The `branch` containing a forking element is called the
"`from-branch`". The `branch` that the forking element points to is called the
"`to-branch`". It is possible for these two branches to be one and the same.
The element in the to-branch that the `Fork` connects to is called the "`to-element`".

`Fork` elements are uni-directional. That is, particles can travel from a `Fork` element
in a `from-branch` to the `to-branch` of the `Fork` but travel cannot happen in
the reverse direction. To get a bi-directional link between branches, use two `Forks` with
the `to-element` of both `Forks` being the other `Fork`.

To avoid ambiguities, the types of `to-elements` are restricted to be one of:
- Marker
- Beginning
- FloorPosition
- Fork
Notice that these types of elements have zero length and unit transfer maps.

A `Fork` element has zero length and must always have a [`ForkP`](#fork.group) parameter group.
The components of the `ForkP` group are:
```{code} yaml
  to_BeamLine           # String: Name of BeamLine to fork to.
  to_Branch             # String: Name of Branch to fork to.
  to_element            # Optional String: Element to fork to. Default is Beginning.
  direction             # Optional Switch: Longitudinal Direction of travel of injected beam.
  Branch_name           # Optional String: Name to give created Branch.
  propagate_reference   # Optional Boolian: Propagate reference species and energy? Default is False.
```
The possible values of the optional `direction` switch are:
```{code} yaml
FORWARDS            # Injected particle propagates in forward (+s) direction. Default.
BACKWARDS           # Injected particle propagates in reverse (-s) direction.
```

The `direction` component of `ForkP` indicates the direction that a particle moving into
the forked-to branch will travel. If `direction` is set to `FORWARDS` (the default)
the direction of travel is downstream (`+s`-direction) and vice versa if `direction` is set to
`BACKWARDS`. Note: It does not make sense to have `direction` set to `BACKWARDS` if the
`to-element` is the `Beginning` element. Similarly, it does not make sense to have `direction`
set to `FORWARDS` if the `to-element` is the end element in the branch.

The `ForkP` group of any given `Fork` element must contain one an only one of `to_BeamLine`
or `to_Branch`. If `to_BeamLine` is present, A new branch is to be created and added to
the `Lattice` set of branches. In this case, `Branch_name` may be set giving the name
of the branch. If `to_Branch` is present, the fork connects to an existing branch. In this case,
`Branch_name` is ignored.

The optional `to_element` component of `ForkP` gives the name of the `to-element`. 
If not present, the default is the `Beginning` element.
The names given by `to_element` must be unique.
The `to-element` may inherit the reference species and energy of the `Fork` element 
if and only if the `to-element` is the `Beginning` element and
the `propagate_reference` component is set to `True` (the default is `False`).
Reference propagation override any reference setting in the `to-element`.

