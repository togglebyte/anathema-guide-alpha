# State

## Example 

Example of internal state

```rust
#[derive(State)]
struct MyState {
    name: StateValue<String>,
    guests: List<String>,
}

struct MyView(MyState);

impl View for MyView {
    fn state(&self) -> &dyn State {
        &self.0
    }
}

```

There are two types of state:
* Internal
* External 
 
## External state

External state is state that is passed to the view from the outside.

A state can either be a direct state from a parent view:
```
// Anathema template
@chid parent_state
```
or a custom map declared in the template:
```
// Anathema template
@myview {"bunnies": list_of_bunnies}
```

## Internal state

Internal state is provided by the `View`, by implementing the `fn state(&self) -> &dyn State` method from the `View` trait.

The state is owned by the view, and the view has mutable access to the state.

A state can contain:

* Primitives, wrapped in `StateValue<T>`
* Collections in the form of `List<T>` (It's redundant to wrap `T` in a `StateValue<T>` as this is done by the `List<T>` itself)
* Maps in the form of `Map<T>` (the keys are `String`s)
* Any other type that implements `State`

A state has to be a struct with named fields.

### Example of a nested internal state

```rust
#[derive(State)]
struct Outer {
    name: StateValue<String>,
    collection: List<String>,
    dict: Map<usize>,
    nested_state: Inner
    many_inners: List<Inner>
}

#[derive(State)]
struct Inner {
    counter: StateValue<i32>
}

impl View for Index {
    fn tick(&mut self) {
        *self.state.nested_state.counter += 1;
    }

}
```

Making a change to the wrapped value of `StateValue<T>` is what causes
the update of the widgets, therefore the `StateValue<T>` should not be replaced, 
but rather changes should be made to the inner value via deref mut:

```rust
*self.state += 1;
```
