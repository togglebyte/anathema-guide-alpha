# Widgets

Even though it's possible to create your own widgets Anathema aims to provide
the necessary building blocks to represent almost any layout.

Widgets that draw them selves (e.g `text`, `span` and `border`) support these default
attributes:

### `foreground` 

Foreground colour

Valid values:
* hex: `#ffaabb`
* string: "green"

### `background` 

Background colour (see `foreground` for valid values)

### `bold`

Valid values:
`true` or `false`

### `italic`

Valid values:
`true` or `false`

## Default widgets

The following is a list of available widgets and their template names:

- [Text](./widgets/text.md) (template name: `text`)
- [Span](./widgets/span.md) (template name: `span`)
- [Border](./widgets/border.md) (template name: `border`)
- [Alignment](./widgets/alignment.md) (template name: `alignment`)
- [VStack](./widgets/vstack.md) (template name: `vstack`)
- [HStack](./widgets/hstack.md) (template name: `hstack`)
- [ZStack](./widgets/zstack.md) (template name: `zstack`)
- [Expand](./widgets/expand.md) (template name: `expand`)
- [Spacer](./widgets/spacer.md) (template name: `spacer`)
- [Position](./widgets/position.md) (template name: `position`)
- [Viewport](./widgets/viewport.md) (template name: `viewport`)
