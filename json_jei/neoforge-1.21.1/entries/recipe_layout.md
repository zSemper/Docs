# Recipe Layout

The recipe layout describes where each ingredient is placed in the category.

The `recipe_layout` object is split between `input` and `output` and use the same syntax.

```json
{
  "recipe_layout": {
    "input": [
      // ingredient list
    ],
    "output": [
      // ingredient list
    ]
  }
}
```

Each ingredient has a `"type"` that describes which ingredient type should be placed.
Json Jei comes with four predefined ingredients:

| Ingredient                                                                           | Type                            |
|--------------------------------------------------------------------------------------|---------------------------------|
| [Item Ingredient](/json_jei/neoforge-1.21.1/entries/ingredients/item.md)             | `"type": "json_jei:item"`       |
| [Fluid Ingredient](/json_jei/neoforge-1.21.1/entries/ingredients/fluid.md)           | `"type": "json_jei:fluid"`      |
| [Energy Ingredient](/json_jei/neoforge-1.21.1/entries/ingredients/energy.md)         | `"type": "json_jei:energy"`     |
| [Experience Ingredient](/json_jei/neoforge-1.21.1/entries/ingredients/experience.md) | `"type": "json_jei:experience"` |

Json Jei also allows new custom ingredients to be added: [Custom Json Ingredient](/json_jei/neoforge-1.21.1/entries/ingredients/custom_ingredient.md).

<br>

Ingredients also require a `"key"` field which is the identifier of the ingredient and used as a lookup in recipes. Each `"key"`
has to be **unique**, there should be no two ingredients and render components that share the same key.

---

## Example

```json
{
  "recipe_layout": {
    "input": [
      {
        "type": "json_jei:item",
        "key": "item_in"
        // specific ingredient values
      }
    ],
    "output": [
      {
        "type": "json_jei:fluid",
        "key": "fluid_out"
        // specific ingredient values
      }
    ]
  }
}
```