# Generate .gitignore files

![Latest Release](https://img.shields.io/github/v/release/archetect-common/dot-gitignore.archetype?style=flat-square&label=Latest%20Release&color=blue)

This is an [Archetect](https://archetect.github.io/) archetype for generating
`.gitignore` files.

## Rendering

To generate content from this Archetype, copy and execute the following command:

```sh
archetect render git@github.com:archetect-common/dot-gitignore.archetype.git#v1
```

## Usage

This archetype is designed to be used as a component library in parent archetypes to generate .gitignore files for multiple
languages and IDEs.

In order to use this archetype, you'll first need to register it as a component in your `archetype.yaml` manifest:

```yaml
---
description: "Example Archetype"
authors: ["John Doe <john.doe@example.com"]
languages: ["Rust"]
frameworks: ["axum", "tracing", "seaorm"]
tags: ["service", "microservice"]

requires:
  archetect: 2.0.0

components:
  gitignore: git@github.com:archetect-common/dot-gitignore.archetype.git#v1
```

Then, you can use this component to render a `.gitignore` file, specifying what `ingores` should be included:

```rhai
let context = #{}

context["project-name"] = prompt("Project Name");

render(Archetype("gitignore"), Path(context["project-name"]), #{
    ignore: ["Rust", "IDEA"]
});
```

Currently supported/implemented `ingores`:

- Rust
- RustBinary
- RustLibrary
- Java
- IDEA
- Eclipse
- Target
