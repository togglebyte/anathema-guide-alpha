# Expand (`expand`)

Expand the widget to fill the remaining space.

The layout process works as follows:
First all widgets that are not `expand` or `spacer` will be laid out.
The remaining space will be distributed between `expand` then `spacer`.

The size is distributed evenly between all `expand`s.

To alter the distribution factor set the `factor` attribute.

## Example

```
border [width: 10, height: 11]
    vstack
        expand
            border
                expand
                    text "top"
        expand
            border
                expand
                    text "bottom"
        text "footer"
```
```
┌────────┐
│┌──────┐│
││top   ││
││      ││
│└──────┘│
│┌──────┐│
││bottom││
││      ││
│└──────┘│
│footer  │
└────────┘
```

## Attributes

### `factor`

The factor decides the amount of space to distribute between the `expand`s.

Given a height of 33 and two `expand` widgets, the height would be divided by
two.

If one of the `expand` widgets had a `factor` of two, then it would receive 22
of the total 33 height, and the remaining widget would receive 11.

### `axis`

Expand along an axis.

Valid values:

* `"horz"` | `"horizontal"`
* `"vert"` | `"vertical"`

### `fill`

Fill the unpainted space with a string.

Example:
```
border [width: 10, height: 5]
    expand [fill: "+-"]
        text "Hello"
```
```
┌────────┐
│Hello-+-│
│+-+-+-+-│
│+-+-+-+-│
└────────┘
```
