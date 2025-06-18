# Libraries

The Particle Accelerator Lattice Standard (PALS) documents objects and their properties.
For readability, this standard uses YAML-style examples.
We exchange PALS lattices often via text files, and PALS can also directly be implemented in-memory in object-oriented programming languages.


## Python

The [PALS-Python](https://github.com/campa-consortium/pals-python) project implements the PALS schema in a file-agnostic way, mirrored in data objects.

PALS-Python provides interfaces to:
* generate lattices,
* write and read from/to files,
* convert files and
* validate existing files.


## More Implementations Wanted!

We welcome community implementations of PALS!
We seek implementations such as readers of PALS-conforming files to Julia/C++/Fortran/etc., visualization of PALS files, and more!
