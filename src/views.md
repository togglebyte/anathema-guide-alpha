# View

A view exposes event handling and passes any internal state to the runtime.
Any type that implements the `anathema::core::View` trait is a view.

This trait has no required methods, however note that
without implementing the `fn state(&self) -> &dyn State` method, no internal
state will be exposed to the template even if the view has a state.

See [State](./templates/state.md) for more information about state.

## Example

```rust
use anathema::core::{Event, KeyCode, Nodes, View};

impl View for MyView {
    fn on_event(&mut self, event: Event, _: &mut Nodes<'_>) -> Event {
        match event {
            Event::KeyPress(KeyCode::Char(c), ..) => {
            }
            Event::KeyPress(KeyCode::Backspace, ..) => {
            }
            _ => {}
        }
        
        event
    }

    fn state(&self) -> &dyn State {
        &self.state
    }

    fn tick(&mut self) {
        *self.state.counter += 1;
    }

    fn focus(&mut self) {
        *self.state.color = Color::Reset;
    }

    fn blur(&mut self) {
        *self.state.color = Color::Magenta;
    }
    
}
```

## Root view

The runtime needs at least one view, however since the `View` trait is
implemented for the unit type it is possible to pass `()` as an argument
instead of your own defined view:

```rust
let view = ();

let template = read_to_string("templates/index.aml").unwrap();

// Pass associate the template with the root view:
let mut templates = Templates::new(template, view);

let templates = templates.compile().unwrap();
let runtime = Runtime::new(&templates).unwrap();
```

This is suitable if no event handling or no internal state is required.

## One or many views

### Singular instance of a view

If the number of instances are known at compile time, for instance the view is not
created inside a for-loop, then use `add_view` to register a view with a
template.

```rust
let items_view = ItemsView::new();

let items_template = read_to_string("templates/index.aml").unwrap();
templates.add_view(
    "items",        // Name of the view in the template
    items_template,  // Template
    items_view       // A view instance
);
```
This is then accessible in the template with the view syntax:
```
@items
```

### Multiple / dynamic instances of a view

If a view is used inside a for-loop or is otherwise generated as requested by
the runtime use `add_prototype`:

```rust
let item_view = ;

let item_template = read_to_string("templates/index.aml").unwrap();
templates.add_prototype(
    "item",             // Name of the view in the template
    item_template,      // Template
    || ItemView::new()  // A closure creating a view instance when called
);
```
This makes it possible to create views on the fly:
```
for item in items
    @item item
```
