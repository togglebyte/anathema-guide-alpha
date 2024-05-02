# Spacer (`spacer`)

The `spacer` widget will fill out any remaining space within a widget.

## Example

```
border
    hstack
        text "Hi"
        spacer
```
```
┌─────────────────────────┐
│Hi                       │
└─────────────────────────┘
```
without the spacer:
```
border
    hstack
        text "Hi"
```
```
┌──┐
│Hi│
└──┘
```
