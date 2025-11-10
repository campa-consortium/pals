(c:conventions)=
# Conventions

%---------------------------------------------------------------------------------------------------
(s:keywords)=
## Keywords

The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD",
"SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be
interpreted as described in [RFC 2119](http://tools.ietf.org/html/rfc2119).

All keywords in this standard are case-sensitive.

%---------------------------------------------------------------------------------------------------
(s:syntax)=
## Syntax Used in this Document

The PALS [schema standard](#s:std.components) does not define any particular language to implement 
a lattice. Rather, there are associated
language specific standards that define grammars for YAML, JSON, Python, etc. Along with these
associated standards, there are packages that implement translation between lattice files and a 
representational internal format defined by the package.

While the standard itself is language agnostic, this document that describes the standard
needs to use some syntax and this syntax is based upon YAML. Non-YAML syntax used here is:

1. The {math}`N^{th}` item in a list is referred to using square brackets enclosing the index: `[N]`.
For example:
```{code} YAML
Aperture:
  name: ap1
  x_limit: [-0.03, 0.04]
```
here `x_limit[1]` and `x_limit[2]` would refer to the first and second values of `x_limit` respectively.

2. Boolean parameters can be one of three values
- `true`
- `false`
- `null`          # Useful as a default value when neither `true` nor `false` is appropriate.

3. The standard defines the following symbols which can be used in place of a value:
- `null`   # Value has not been set: use for open limits, etc.
- `Inf`    # Infinity
- `-Inf`   # Negative infinity
- `NaN`    # Not a number

Note: There is a difference between
```{code} yaml
this_group:
  key1: value1
  key2: value2
  key3: value3
```
and
```{code} yaml
this_group:
  - key1: value1
  - key2: value2
  - key3: value3
```
The first represents an unordered dictionary of key-value pairs and the second represents an ordered 
dictionary of key-value pairs. 

Note: the actual syntax in some particular language that is used to 
represent an unordered dictionary may be an ordered dictionary. That is, the standard does not
prohibit ordered dictionaries being used in place of unordered dictionaries. However, ordered
dictionaries must always be used for things that the standard defines as an ordered dictionary.
In fact, when there is a choice of using an ordered or an unordered dictionary,
an ordered dictionary may be preferred to maintain human readability. An example of this is with
lattice element attribute dictionaries where having the name of the element as the first attribute
enhances legibility. 

%---------------------------------------------------------------------------------------------------
(s:parameters)=
## Parameters

All parameters are optional unless explicitly stated otherwise.
Optional real or integer parameters have a default value of zero unless otherwise stated.
Optional string parameters have a default value of blank unless otherwise stated.

%---------------------------------------------------------------------------------------------------
(s:includefiles)=
## Include Files

A lattice file can include other lattice files using an include statement.
```{code} yaml
include: <file-name>
```
where `<file-name>` is the name of the file to be included.

%---------------------------------------------------------------------------------------------------
(s:names)=
## Names

Many constructs in the standard like lattice elements, branches, parameter groups, etc., may have
an associated name. To ensure seamless translation to particular languages, all names must conform
to the following:
- A name must start with a letter or the underscore character
- A name cannot start with a number
- A name can only contain alpha-numeric characters and underscores (A-Z, a-z, 0-9, and _ )

%---------------------------------------------------------------------------------------------------
(s:element.matching)=
## Element Name Matching

Lattice element name matching is the process of finding the set of lattice elements that 
are matched to a given string. Name matching is important in a number of instances including
lattice expansion where there are [`Fork`](#s:forking) elements and for evaluating mathematical
expressions.

The simplist form of name matching is if the string matches
the `name` field of an element or elements. Regular expressions can be used. 
Regular expressions must conform to the [PCRE2](https://www.pcre.org/) standard. 

The names of an element may be "qualified" by prepending a `branch` or `BeamLine` name to the string
using the string `">>"` as a separator. For example, `"B1>>Qaf.*"` would match
to all elements in a branch or BeamLine named `"B1"` whose name begins with `"Qaf"`.

Element matches may be restricted to a given element kind using the notation
```{code} yaml
<kind>::<name>
```
where `<kind>` is the element kind and `<name>` is the element name.
Example:
```{code} yaml
Marker::bpm.
```
This will match to all `Marker` elements whose name is four characters starting with `bpm`.

If the match string ends with the character `"#"` followed by an integer `N`,
this will match to the `N`{sup}`th` instance matched to in any `branch` or `BeamLine`.
For example, `"Sd#3"` will match to the 3{sup}`rd` instance of all elements named
`"Sd"`.

Lattice elements can also be referred to by the index in which they appear in a branch
with the first element having index one, etc. Branches do not get an index since the
PALS standard does not mandate that the branches of a lattice be stored in an array (it
could, for example, be a linked list).

Elements can be matched using a range construct which has the form
```{code} yaml
<ele1>:<ele2>
```
where `<ele1>` marks the beginning of the range and `<ele2>` marks the end of the range.
Example:
```{code} yaml
Q1:Q2
```
In this example, the range matches all elements from `Q1` to `Q2` inclusive of `Q1` and `Q2`.
If `<ele2>` comes before `<ele1>` the range "wraps around" the branch or beamline.
For example, if `Q2` comes before `Q1` in the above example, the range matches all elements from
`Q1` to the end of the line plus all elements from the beginning of the line to `Q2`.

Commas `,` can be used to form the union of element sets. The syntax is
```{code} yaml
<element-set1>, <element-set2>, ... , <element-setN>
```
where `<element-set1>`, ... `<element-setN> are element sets. 
Example:
```{code} yaml
A, B, Q.*
```
This will match to all elements named `A`, `B`, and all elements whose name begins with `Q`.

Ampersands `&` can be used to form the intersection of element sets. The syntax is
```{code} yaml
<element-set1> & <element-set2> & ... & <element-setN>
```
where `<element-set1>`, ... `<element-setN> are element sets. 
Example:
```{code} yaml
Marker::.* & Q1:Q2
```
This will match to all `Marker` elements that are in the range from `Q1` to `Q2`.

%---------------------------------------------------------------------------------------------------
(s:parameter.matching)=
## Element Parameter Name Matching

For element parameters, the general syntax is
```{code} yaml
<beamline>>><element>><parameter-group>.<sub-group1>. ... .<sub-groupN>.<parameter>
```
where
```{code} yaml
<beamline>:                     # Optional BeamLine or Branch name.
<element>                       # Optional lattice element name.
<parameter-group>               # Parameter group name.
<sub-group1>. ... .<sub-groupN> # Subgroups if they exist.
<parameter>                     # Parameter name.
```
Only `<beamline>` and `<element>` use PCRE2 syntax. 

Example:
```{code} yaml
Qa.*>MagneticMultipoleP.Ks2L
```
This will match the `Ks2L` component of all elements whose name begins with `Qa`. Notice that
since only `<beamline>` and `<element>` use PCRE2 syntax, the dot separatingthe parameter group
and the parameter is unambiguous.

%---------------------------------------------------------------------------------------------------
(s:units)=
## Units

The lattice standard uses SI except for energy which uses `eV`.
```{list-table} Units used by the Standard
:width: 60%
:header-rows: 1

* - Quantity
  - Units
* - charge
  - fundamental charge
* - length
  - meters
* - time
  - seconds
* - energy
  - eV
* - momentum
  - eV/c
* - mass
  - eV/c^2
* - voltage
  - Volts
* - angles and phases
  - radians / 2 {math}`\pi`
* - magnetic field
  - Tesla
* - frequency
  - Hz
* - electric field
  - Volts/m
```

%---------------------------------------------------------------------------------------------------
(s:constants)=
## Constants

Constants defined by PALS:
```{code} yaml
c_light                   # [ m/sec] Speed of light
h_planck                  # [eV*sec] Planck's constant
h_bar_planck              # [eV*sec] Reduced Planck's constant
r_e                       # [m] Classical electron radius
r_p                       # [m] Classical proton radius
e_charge                  # [Coul] Elementary charge
mu_0_vac                  # [eV*sec^2/m] Vacuum permeability
eps_0_vac                 # [1/eV*m] Permittivity of free space
classical_radius_factor   # [m*eV] Classical Radius Factor: 1/(4 pi epsilon_0 c^2)
fine_structure_const      # [-] Fine structure constant
n_avogadro                # [-] Avogadro's constant
```
The `classical_radius_factor` is a useful number when converting a formula that involve the classical
electron or proton radius to a formula for something other than an electron or proton.

%---------------------------------------------------------------------------------------------------
(s:functions)=
## Functions

Functions defined by PALS:
```{code} yaml
sqrt(x)                  # Square Root
log(x)                   # Logarithm
exp(x)                   # Exponential
sin(x), cos(x)           # Sine and cosine
tan(x), cot(x)           # Tangent and cotangent
sinc(x)                  # Sin(x)/x Function
asin(x), acos(x)         # Arc sine and Arc cosine
atan(x)                  # Arc tangent
atan2(y, x)              # Arc tangent of y/x
sinh(x), cosh(x)         # Hyperbolic sine and cosine
tanh(x), coth(x)         # Hyperbolic tangent and cotangent
asinh(x), acosh(x)       # Hyperbolic arc sine and Arc cosine
atanh(x), acoth(x)       # Hyperbolic arc tangent and cotangent
abs(x)                   # Absolute Value
factorial(n)             # Factorial
ran()                    # Random number between 0 and 1
ran_gauss()              # Gaussian distributed random number
ran_gauss(sig_cut)       # Gaussian distributed random number
int(x)                   # Nearest integer with magnitude less then x
nint(x)                  # Nearest integer to x
sign(x)                  # 1 if x positive, -1 if negative, 0 if zero
floor(x)                 # Nearest integer less than x
ceiling(x)               # Nearest integer greater than x
modulo(a, p)             # a - floor(a/p) * p. Will be in range [0, p).
mass_of(A)               # Mass of particle A
charge_of(A)             # Charge, in units of the elementary charge, of particle A 
anomalous_moment_of(A)   # Anomalous magnetic moment of particle A
```
