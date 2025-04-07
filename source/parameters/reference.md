%---------------------------------------------------------------------------------------------------
(s:ref.params)=
## ReferenceP: Reference Parameters

In Construction...

The `ReferenceP` parameter group contains parameters for describing the reference energy,
species, and time. 
The components of this group are:
```{code} yaml
species_ref          - Reference species.
pc_ref               - Reference momentum*c.
E_tot_ref            - Reference total energy.
time_ref             - Reference time.
location             - Where reference parameters are evaluated.
```

The `location` component records where the reference parameters are evaluated at.
Possible values are
```{code} yaml
UPSTREAM_END    - Upstream end of the element.
DOWNSTREAM_END  - Downstream end of the element.
```
Except for `time_ref`, the reference parameters are generally the same at the
upstream and downstream ends of the element. However, there are exceptions.
For example, the upstream and downstream `species_ref` for a `Foil` element 
will generally be different. And the reference energy will change if the
`dE_ref` component of the [`ReferenceChangeP`](#s.ref.change.params) group is nonzero.
See the [`ReferenceChangeP`](#s.ref.change.params) for details as how the reference
energy and time is computed.

For a `BeginningEle` element, parameters of this group are user settable.
For all other element kinds, the parameters of this
group are calculated by  and are not user settable.
