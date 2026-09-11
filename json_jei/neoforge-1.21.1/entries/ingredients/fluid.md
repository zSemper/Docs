# Fluid Ingredient

The fluid ingredient describes a fluid with various options to choose how its
displayed in jei.


![Fluid Ingredient](/json_jei/assets/ingredient/fluid.png)

<br>

Possible changeable values:

| Value            | Explanation                                                                    | Default Value | Example                  |
|------------------|--------------------------------------------------------------------------------|---------------|--------------------------|
| `x`              | The x position of the fluid ingredient.                                        | `0`           | `"x": 45`                |
| `y`              | The y position of the fluid ingredient.                                        | `0`           | `"y": 19`                |
| `capacity`       | The total capacity of the ingredient. Changes how much is rendered in jei.     | `1`           | `"capacity": 4000`       |
| `show_tooltip`   | Shows the `x / y mB` tooltip. Only shown when `capacity` is set.               | `false`       | `"show_tooltip": true`   |
| `width`          | The width of the rendered fluid.                                               | `16`          | `"width": 16`            |
| `height`         | The height of the rendered fluid.                                              | `16`          | `"height": 32`           |
| `has_background` | Renders the background of the ingredient. Useful when category has to texture. | `false`       | `"has_background": true` |
| `has_overlay`    | Renders an overlay onto the ingredient.                                        | `false`       | `"has_overlay": true`    |

---

## Full Example

Set in the category:

```json
{
  "type": "json_jei:fluid",
  "key": "fluid_ingredient",
  "x": 45,
  "y": 19,
  "capacity": 4000,
  "show_tooltip": true,
  "width": 16,
  "height": 32,
  "has_background": true,
  "has_overlay": true
}
```

<br>

Set in the recipe as input:

```json
{
  "fluid_ingredient": {
    // can also be a "tag"
    "fluid": "minecraft:water",
    "amount": 100
  }
}
```

And for output:

```json
{
  "fluid_ingredient": {
    "id": "minecraft:water",
    "amount": 100,
    "components": {
      // optional field, not required
    }
  }
}
```