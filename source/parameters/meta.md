%---------------------------------------------------------------------------------------------------
(s:meta.params)=
## MetaP: Metadata Parameters

`MetaP` has four standard components
```{code} yaml
  alias         # String
  ID            # String
  label         # String
  description   # String
```
In addition to an element's name, these strings can be used for pattern matching
when trying to locate all elements of a given type.

Besides the four standard strings, the `MetaP` parameter group can be used to store metadata 
that describes the lattice element but is not part of the PALS standard. 
Such data is necessarily program dependent.
Example metadata could be blueprint information, information on power supply connections, etc.

Components of `MetaP` are not limited to being simple strings or numbers but can be complex 
structures. The information contained in `MetaP` should be restricted to information that 
does not affect simulations. Custom, program specific information should be stored elsewhere.
Example:
```{code} yaml
Metap:
  ID: 0137-85
  history:                  # Custom information
    - manufacture: 2017-03-07
    - installed: 2018-01-23
    - ...     
```


