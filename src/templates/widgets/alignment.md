# Alignment (`alignment`)

Alignment will inflate the wrapping widget if any `align` value is given other
than `"top-left"`.

## Example

```
border [width: 16, height: 5]
    alignment [align: "centre"]
        text "centre"
```
```
┌──────────────┐
│              │
│    centre    │
│              │
└──────────────┘
```

## Attributes

### `align`

Valid values:
* `"top-left"`
* `"top"`
* `"top-right"`
* `"right"`
* `"bottom-right"`
* `"bottom"`
* `"bottom-left"`
* `"left"`
* `"centre"` or `"center"`
