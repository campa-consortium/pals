%---------------------------------------------------------------------------------------------------
(s:fork.params)=
## ForkP: Fork Parameters

The `ForkP` parameter group holds parameters for a `Fork` element.
The components of this group are:
```{code} yaml
  to_line               # String: Beam line to fork to
  to_ele                # String: Element forked to.
  direction             # Switch: Longitudinal Direction of travel of injected beam.
  propagate_reference   # Boolian: Propagate reference species and energy?
```
The possible values of the optional `direction` switch are:
```{code} yaml
FORWARDS            # Injected particle propagates in forward direction. Default.
BACKWARDS           # Injected particle propagates in reverse direction.
```

See the [](#s:forking) chapter for more details.

