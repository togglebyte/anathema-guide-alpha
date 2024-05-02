# Getting started

## Install
Add `anathema` to your Cargo.toml file.

```toml
...
[dependencies]
anathema = { git = "https://github.com/togglebyte/anathema" }
```

### Note

This guide is written against the current version on [Github](https://github.com/togglebyte/anathema). 
Even though efforts are made to keep this guide up to date there are
possibilities of changes being made and published before they reach
this guide.

At the time of writing, Anathema should be considered alpha.

## A basic example

Render a border around the text, placing the text in the middle of the
terminal.

```rust
// src/main.rs
use std::fs::read_to_string;

use anathema::runtime::Runtime;
use anathema::vm::Templates;

fn main() {
    // Step one: Load and compile templates
    let template = read_to_string("templates/index.aml").unwrap();
    let mut templates = Templates::new(template, ());
    let templates = templates.compile().unwrap();

    // Step two: Runtime
    let runtime = Runtime::new(&templates).unwrap();

    // Step three: start the runtime
    runtime.run().unwrap();
}
```

```
// templates/index.aml
alignment [align : "center"]
    border [foreground: "cyan"]
        text [foreground: #fa0] "Hello world"
```
