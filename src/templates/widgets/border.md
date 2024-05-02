# Border (`border`)

## Example

```
border
    text "What a border!"
```
```
┌──────────────┐
│What a border!│
└──────────────┘
```

## Attributes

### `width`

The fixed width of the border

### `height`

The fixed height of the border

### `min-width`

The minimum width of the border

### `min-height`

The minimum height of the border

### `sides`

Valid values:
* `"top"`
* `"right"`
* `"bottom"`
* `"left"`

Sides specifies which sides of the border should be drawn.

This can be written as an individual side:

```
border [sides: "left"]
    text "What a border!"
```
```
│What a border!
```
or
```
border [sides: "left"]
    text "What a border!"
```
```
──────────────
What a border!
```

It can also be written as a list:
```
border [sides: ["left", "top"]]
    text "What a border!"
```
```
┌──────────────
│What a border!
```

### `border-style`

The default border style is `"thin"`.

For a thicker border style the value `"tick"` can be used:

```
border [border-style: "thick"]
    text  "What a border!"
```
```
╔══════════════╗
║What a border!║
╚══════════════╝
```

It's also possible to customise the border style by providing an eight character
string as input, where each character represents a portion of the corner in the 
following order:

1. top left
2. top
3. top right
4. right
5. bottom right
6. bottom
7. bottom left
8. left

See the following example:

```
border [border-style: "12345678"]
    text  "What a border!"
```
```
1222222222222223
8What a border!4
7666666666666665
```

