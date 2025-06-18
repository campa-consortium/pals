# File Formats

The Particle Accelerator Lattice Standard (PALS) documents objects and their properties.
For readability, this standard uses YAML-style examples, but the PALS schema can be implemented in a variety of file formats.


## File Endings

When storing a PALS lattice in a file, please use the following self-describing file endings.

* [YAML](https://yaml.org/faq.html): `.pals.yaml`
* [JSON](https://www.json.org/json-en.html): `.pals.json`
* [TOML](https://toml.io): `.pals.toml`
* [XML](https://en.wikipedia.org/wiki/XML): `.pals.xml`


## Schema Files

We have not yet developed schema files for validation.
So far, we develop a tool for file validation that is based on the pydantic, see the *Libraries* section.
