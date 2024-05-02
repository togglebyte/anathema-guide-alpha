# Span (`span`)

The `span` widget is used to style text on the same line.
Span can not be used on its own, it has to belong to a `text` widget.

```
text "start"
    span "-middle-"
    span "end"
```

```
start-middle-end
```

The `span` widget can be styled using the standard attributes, such as `bold`,
`foreground` etc.
