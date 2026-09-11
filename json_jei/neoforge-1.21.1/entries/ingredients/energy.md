# Energy Ingredient

The energy ingredient is a custom ingredient by Json Jei. It can be displayed in various
ways and fill level with the provided textures.

![Energy Ingredient](/json_jei/assets/ingredient/energy.png)

<br>

Possible changeable values:

| Value            | Explanation                                                                       | Default Value | Example                  |
|------------------|-----------------------------------------------------------------------------------|---------------|--------------------------|
| `x`              | The x position of the energy ingredient.                                          | `0`           | `"x": 42`                |
| `y`              | The y position of the energy ingredient.                                          | `0`           | `"y": 17`                |
| `capacity`       | The total capacity of the energy ingredient. Changes how much is rendered in jei. | `1`           | `"capacity": 10000`      |
| `show_tooltip`   | Shows the `x / y FE` tooltip. Only shown when `capacity` is set.                  | `false`       | `"show_tooltip": true`   |
| `width`          | The width of the ingredient.                                                      | `16`          | `"width": 12`            |
| `height`         | The height of the ingredient.                                                     | `16`          | `"height": 32`           |
| `has_background` | Renders the background of the ingredient. Useful when category has to texture.    | `true`        | `"has_background": true` |

---

## Full Example

Set in the category:

```json
{
  "type": "json_jei:energy",
  "key": "energy",
  "x": 42,
  "y": 17,
  "capacity": 10000,
  "show_tooltip": true,
  "width": 12,
  "height": 32,
  "has_background": true
}
```

<br>

Set in the recipe:

```json
{
  "energy": 1000
}
```