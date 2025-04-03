%---------------------------------------------------------------------------------------------------
(s:meta.params)=
## MetaP: Metadata Parameters

The `MetaP` parameter group can be used for metadata that describes the lattice element
but is not part of the PALS standard. Such data is necessarily program dependent.
Example metadata could be blueprint information, information on power supply connections, etc.
Example:
```{code} yaml
MetaP:
  alias:  an_alternative_name
  Meta: Mark 4 quadrupole
```

Components of `MetaP` are not limited to being simple strings or numbers but can be complex 
structures. The information contained in `MetaP` should be restricted to information that 
does not affect simulations. Custom, program specific information should be stored elsewhere.

