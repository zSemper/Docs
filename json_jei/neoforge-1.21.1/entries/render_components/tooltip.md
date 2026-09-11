# Tooltip Render Component

The tooltip component is an invisible field that can be hovered over to show a single or multiple lines of text.

| Value     | Explanation                                                                                              | Default Value | Reference Key              | Example                                 |
|-----------|----------------------------------------------------------------------------------------------------------|---------------|----------------------------|-----------------------------------------|
| `tooltip` | Holds the lines that get shown when hovering over it. They can either be plain text or translation keys. |               | `$(s:[key])` For each line | `"tooltip": [ "Line 1", "$(s:line2)" ]` |
| `x`       | Describes where on the x axis the tooltip field is placed.                                               | `0`           | `$(i:[key])`               | `"x": 10`                               |
| `y`       | Describes where on the y axis the tooltip field is placed.                                               | `0`           | `$(i:[key])`               | `"y": 10`                               |
| `width`   | Describes how wide the tooltip field is.                                                                 | `1`           | `$(i:[key])`               | `"widht": 16`                           |
| `height`  | Describes how large the tooltip field is.                                                                | `1`           | `$(i:[key])`               | `"height": 16`                          |

## Example

```json
{
  "type": "json_jei:tooltip",
  "key": "tooltip_key",
  "tooltip": [
    "Line 1",
    "$(s:line2)"
  ],
  "x": 10,
  "y": 10,
  "width": 16,
  "height": 16,
  "values": {
    "line2": "example.gui.tooltip_translation"
  }
}
```