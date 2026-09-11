# Text Render Component

The text render component is a simple text displayable in a category

| Value    | Explanation                                                                               | Default Value | Reference Key | Example                  |
|----------|-------------------------------------------------------------------------------------------|---------------|---------------|--------------------------|
| `text`   | Holds the text that will be rendered. This can either be plain text or a translation key. |               | `$(s:[key])`  | `"text": "Example text"` |
| `x`      | Describes where on the x axis the text is rendered.                                       | `0`           | `$(i:[key])`  | `"x": 10`                |
| `y`      | Describes where on the y axis the text is rendered.                                       | `0`           | `$(i:[key])`  | `"y": 10`                |
| `color`  | Allows for changing the color of the text, in form of a hex color.                        | `"0x3F3F3F"`  | `$(s:[key])`  | `"color": "#00ffff"`     |
| `shadow` | Renders the underlying shadow of the text.                                                | `true`        | `$(b:[key])`  | `"shadow": false`        |

## Example

```json
{
  "type": "json_jei:text",
  "key": "text_key",
  "text": "Example text",
  "x": 10,
  "y": 10,
  "color": "0x00FFFF",
  "shadow": false
}
```