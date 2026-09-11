# Item Render Component

Renders a simple item with item decoration (item count, durability, etc.) into the category, allowing an amount and data components.

| Value  | Explanation                         | Default Value | Reference Key | Example                                         |
|--------|-------------------------------------|---------------|---------------|-------------------------------------------------|
| `item` | The item stack to render            |               |               | `"item": { "id": "minecraft:dirt", "count": 2}` |
| `x`    | The x position of the rendered item | `0`           | `$(i:[key])`  | `"x": 10`                                       |
| `y`    | The y position of the rendered item | `0`           | `$(i:[key])`  | `"y": 30`                                       |

## Example

```json
{
  "type": "json_jei:item",
  "key": "item_key",
  "item": {
    "id": "minecraft:dirt",
    "count": 2
  },
  "x": 10,
  "y": 30
}
```