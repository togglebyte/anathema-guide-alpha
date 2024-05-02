# Position (`position`)

Position the widget relative to its parent.

## Example

```
border [width: 10, height: 5]
    position [top: 1, left: 1]
        text "Hi"
```
```
┌────────┐
│        │
│ Hi     │
│        │
└────────┘
```

To position a widget on top of another widget combine the `position` widget with
a `zstack`:

```
zstack
    border [width: 10, height: 5]
    position [top: 0, left: 2]
        text "] Hi ["
```
```
┌─] Hi [─┐
│        │
│        │
│        │
└────────┘
```

## Attributes

### `left` 

Position the **left** side of the widget with an offset of the given value.

### `right` 

Position the **right** side of the widget with an offset of the given value.

```
border [width: 10, height: 5]
    position [top: 0, right: 0]
        text "Hi"
```
```
┌────────┐
│      Hi│
│        │
│        │
└────────┘
```

### `top` 

Position the **top** side of the widget with an offset of the given value.

### `bottom` 

Position the **bottom** side of the widget with an offset of the given value.
