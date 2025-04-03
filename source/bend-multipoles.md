(c:multipole.bend)=
# Multipole Fields in a Bend

In Construction...

%- **exact_multipoles**
%The `exact_multipoles` switch can be set to one of:
%  ```{code} yaml
%  off                 ! Default
%  vertically_pure
%  horizontally_pure
%  ```
%  This switch determines if the multipole fields, both magnetic and electric, and including the
%  `k1` and `k2` components, are corrected for the finite curvature of the reference orbit in a
%  bend. See [](#s:field.exact) for a discussion of what `vertically` pure versus
%  `horizontally` pure means. Setting `exact_multipoles` to `vertically_pure` means that the
%  individual {math}`a_n` and {math}`b_n` multipole components are used with the vertically pure solutions
%  begin{equation}
%  bfB = sum_{n = 0}^infty left[ frac{a_n}{n+1} nabla phi_n^r + frac{b_n}{n+1} nabla phi_n^i right], qquad
%  bfE = sum_{n = 0}^infty left[ frac{a_{en}}{n+1} nabla phi_n^i + frac{b_{en}}{n+1} nabla phi_n^r right]
%  end{equation}
%  and if `exact_multipoles` is set to `horizontally_pure` the horizontally pure solutions
%  {math}`psi_n^r` and {math}`psi_n^i` are used instead of the vertically pure solutions {math}`phi_n^r` and
%  {math}`phi_n^i`.