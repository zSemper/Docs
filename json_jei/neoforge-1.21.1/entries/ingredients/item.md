# Item Ingredients

The item ingredient describes a basic item you see in almost all recipes.

![Item Ingredient](/json_jei/assets/ingredient/item.png)

<br>

Possible changeable values:

| Value            | Explanation                                                                    | Default Value | Example                       |
|------------------|--------------------------------------------------------------------------------|---------------|-------------------------------|
| `x`              | Describes the x position where the item is placed.                             | `0`           | `"x": 1`                      |
| `y`              | Describes the y position where the item is placed.                             | `0`           | `"y": 37`                     |
| `has_background` | Renders the slot texture behind the item. Useful when category has no texture. | `false`       | `"has_background": true`      |

---

## Full Example

Set in the category:

```json
{
  "type": "json_jei:item",
  "key": "my_item_ingredient",
  "x": 1,
  "y": 37,
  "has_background": true
}
```

<br>

Set in the recipe as input:

```json
{
  "my_item_ingredient": {
    // can also be a "tag"
    "item": "minecraft:cobblestone",
    "count": 8
  }
}
```

And for output:

```json
{
  "my_item_ingredient": {
    "id": "minecraft:cobblestone",
    "count": 8,
    "components": {
      // optional field, not required
    }
  }
}
```