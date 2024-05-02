# Viewport (`viewport`)

The viewport allows the widgets to overflow in a given direction.

It's important to note that the `viewport` is an unbounded widget.
This means that widgets can be laid out indefinitely along a given axis.

## Example

```
border [height: 4, width: 10]
    viewport [offset: 2]
        text "1"
        text "2"
        text "3"
        text "4"
```
```
┌────────┐
│3       │
│4       │
└────────┘
```

## Attributes

### `direction`

Specifies the direction to lay out the widgets.

Default value: `"forwards"`

Valid values:
* `"backwards"` or `"backward"`
* `"forwards"` or `"forward"`

```
border [height: 5, width: 10]
    viewport [direction: "backward"]
        text "1"
```
```
┌────────┐
│        │
│        │
│1       │
└────────┘
```

### `axis`

Specify along which axis to layout the widgets.

Valid values:

* `"horz"` | `"horizontal"`
* `"vert"` | `"vertical"`


### `offset`

Offset the widgets.
See the example at the top.

### `clamp`

Clamp the offset preventing the last widget from being drawn outside of the
viewport.

**Note**: this feature is currently broken
