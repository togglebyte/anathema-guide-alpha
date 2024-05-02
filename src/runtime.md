# Runtime

```rust
use anathema::runtime::Runtime;

let mut runtime = Runtime::new(&templates).unwrap();
runtime.enable_alt_screen = false;
runtime.fps = 12;
runtime.enable_tabindex = false;
```

## Configuring the runtime

The following settings are available:

### `enable_mouse`

Default: `false`

Enable mouse support in the terminal (if it's supported).


### `enable_alt_screen`

Default: `true`

Creates an alternate screen for rendering. 
Restores the previous content of the terminal to the previous state 
when the runtime ends.

### `enable_ctrlc`

Default: `true` 

If this is disabled then pressing control + c does nothing.

### `enable_tabindex`

Default: `true`

Give a view a `tabindex` value to be able to tab to the view. 
Read more about `tabindices` under [Views](./views.md).

### `fps`

Default: `30`

The number of frames to render per second.

