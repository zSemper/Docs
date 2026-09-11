# Experience Ingredient

The experience ingredient is a custom ingredient by Json Jei. It is rendered as a xp orb
and shows the set xp in the recipe. The color of the amount changes depending on how much xp 
the player has and if its an input ingredient.

![Experience Ingredient](/json_jei/assets/ingredient/experience.png)

<br>

Possible changeable values:

| Value             | Explanation                                                     | Default Value | Example                   |
|-------------------|-----------------------------------------------------------------|---------------|---------------------------|
| `x`               | The x position of the ingredient.                               | `0`           | `"x": 18`                 |
| `y`               | The y position of the ingredient.                               | `0`           | `"y": 43`                 |
| `colored_tooltip` | Changes the color of the tooltip based on the players xp level. | `true`        | `"colored_tooltip": true` |

---

## Full Example

Set in the category:

```json
{
  "type": "json_jei:experience",
  "key": "xp",
  "x": 18,
  "y": 43,
  "colored_tooltip": true
}
```

<br>

Set in the recipe:

```json
{
  "xp": 16
}
```