(c:element.parameters)=
# Element Parameters

Lattice elements parameters are organized into **parameter groups**. 
All groups are organized as abstract syntax trees.
At the top level, there are the groups with names like 
`MagneticMultipoleP`, `ElectricMultipoleP`, `MetaP`, `AlignmentP`, etc. 
By convention, group names use upper camel case and it is highly recommended that this convention
be followed but it is not mandatory. Also, by convention, parameter groups end with a `P`.
This is to distinguish between element kinds and parameter groups which might
have similar names. For example, `Fork` is the name of an element kind and `ForkP`
is the name of a parameter group which a `Fork` element will have.

There are three element parameters that are so common, and do not fit into
any of the parameter groups, that they are not grouped. 
These element parameters are `Length` (element length), `name` (name of element),
and `s_position` (the longitudinal position of the element).

For any given element, a given parameter group can only appear once. For example,
the following is not allowed:
```{code} yaml
Quadrupole:
  name: q10w
  MetaP: ...
  MetaP: ...    # Second instance not allowed!
```

%---------------------------------------------------------------------------------------------------
## Naming and Inheriting Parameters

Any group can be given a **name** and the values can be used in another group of the same type
using **import**.
For example:
```{code} yaml
ApertureP:
  name: ap1
  x_limit: [-0.03, 0.04]
```
The above defines an aperture with the name **ap1**. 
```{code} yaml
ApertureP:
  name: ap2
  inherit: ap1
  y_limit: [-0.02, 0.05]
```
And the above defines a new aperture group which inherits from **ap1**.

Naming a parameter group is only needed if the parameter group is defined outside of an element.
```{code} yaml
Element:
  name: q1
  ApertureP: 
    x_limit: [-0.03, 0.04]
    y_limit: [-0.02, 0.03]
```
And an element can inherit a parameter group from another element:
```{code} yaml
Element:
  name: q2
  ApertureP:
    inherit: q1.ApertureP
```

For an element to inherit all parameter groups from another element, just inherit the element itself:
```{code} yaml
Element:
  name: q3
  inherit: q2
```

%---------------------------------------------------------------------------------------------------
## User Settable (Input) and Dependent (Output) parameters.

Some parameters are set in the lattice file. These parameters are called "User settable" or "input". 
Some parameters will be computed by the Translator during lattice expansion. These parameters are called "dependent" or "output" parameters. There is a third class of parameters that can be an input
parameter if it is set in the lattice file or will be an output parameter if not set.

For example, the `FloorP` parameters can be set for the `BeginningEle` element which is the
first element of any branch line. For most other elements, the `FloorP` parameters can
be calculated starting at the `BeginningEle` and working forward computing the floor parameters
element-by-element.

%---------------------------------------------------------------------------------------------------

```{include} parameters/ackicker.md
```

```{include} parameters/aperture.md
```

```{include} parameters/beambeam.md
```

```{include} parameters/bend.md
```

```{include} parameters/bodyshift.md
```

```{include} parameters/electricmultipole.md
```

```{include} parameters/floor.md
```

```{include} parameters/fork.md
```

```{include} parameters/girder.md
```

```{include} parameters/initialparticle.md
```

```{include} parameters/magneticmultipole.md
```

```{include} parameters/meta.md
```

```{include} parameters/patch.md
```

```{include} parameters/reference.md
```

```{include} parameters/referencechange.md
```

```{include} parameters/rf.md
```

```{include} parameters/solenoid.md
```

```{include} parameters/tracking.md
```


