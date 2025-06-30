%---------------------------------------------------------------------------------------------------
(s:ref.change.params)=
## ReferenceChangeP: Change in Reference Parameters

The `ReferenceChangeP` parameter group contains parameters for describing how the reference energy,
and time deviate from the nominal values from one end of an element to the other end.
The components of this group are:
```{code} yaml
extra_dtime_ref      - Reference time deviation from nominal.
dE_ref               - Change in reference energy.
```
The reference energy and time are stored in the [`ReferenceP`](#s:ref.params) group.

The exit end reference energy
is calculated from the entrance via
```{code} yaml
E_tot_ref(exit) = E_tot_ref(entrance) + dE_ref
```
Notice that this formula is formulated with respect to the entrance and exit ends of the
element as opposed to the upstream and downstream ends. This is done so that reversing
an element longitudinally reverses the change in reference energy.

The downstream reference time is calculated via
```{code} yaml
time_ref(downstream) = time_ref(upstream) + transit_time + extra_dtime_ref
```
where `transit_time` is the time to transit the element assuming a straight line trajectory
and a linear energy change throughout the element. The formula
for the transit time is
```{code} yaml
transit_time = length * (E_tot_ref(upstream) + E_tot_ref(downstream)) / 
                            (c * (pc_ref(upstream) + pc_ref(downstream)))
```
where `length` is the length of the element and `c` is the speed of light.
For elements where there is no energy
change (`dE_ref` = 0), the transit time calculation simplifies to
```{code} yaml
transit_time = length / (beta_ref * c)
```
where `beta_ref` is the normalized particle velocity

The `extra_dtime_ref` parameter in the above is ment as a correction to take into account
for particle motion that is not straight or acceleration that is not linear in energy. For example,
in a wiggler, `extra_dtime_ref` can be used to correct for the oscillatory nature of the
particle trajectories.
Since the PALS standard does not define how tracking is to be done, `extra_dtime_ref` and `dE_ref`
must be calculated by the User.

