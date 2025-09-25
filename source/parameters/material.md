(s:material.params)=
## MaterialP:  Definition of materials

The definition of materials is inspired by Geant4's material handling. One can either use the name, which is the symbol of an element (`"G4_Cu"`, `"G4_H"`, ...) or compound (`"G4_STAINLESS-STEEL"`).
In the future all elements and materials in the [G4 Manual](https://geant4-userdoc.web.cern.ch/UsersGuides/ForApplicationDeveloper/html/Appendix/materialNames.html) will be supported.

Alternatively custom elements can be defined by

```
ElementP:
- name:      # [string] The name of the material
- density:   # [g/cm^3] The density of the material
- Z:         # [int]    The atomic number
- A:         # [int]    The mass number (equals Z+N)
- N:         # [int]    The neutron number
- m:         # [g/mol]  The atomic mass
```

and compunds by

```
CompundP:
- name:      # [string] The name of the material
- density:   # [g/cm^3] The density of the material
- elements:  # List of MaterialP
- ratio:    # List of ratios of the elements
```

### Examples
`MaterialP: "G4_Cu"` or `MaterialP: "G4_STAINLESS-STEEL"` or define a new material.

Liquid deuterium can be defined with the `ElementP` parameters:
```
MaterialP:
- name: "Deuterium(l)"
- density: 0.16
- Z: 1
- A: 1
- m: 2.01
```
and deuterated polyethylene (C2H4) can be defined based on the previous definition
```
MaterialP:
- name: "deutPE"
- density: 1.05
- elements:
  - "G4_C"
  - "Deuterium(l)"
- ratio:
  - 2
  - 4
```


