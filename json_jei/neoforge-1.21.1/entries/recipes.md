# Recipes

The structure of custom recipes is similar to the normal recipe structure, meaning it requires a `"type"` value, 
which is the `"uid"` of the category.

To set the contents of ingredients the set `"key"` is used. If a key is missing or misspelled, it will be treated as 
a not required field and the content will not be set. 

While energy and experience ingredients use a single number, item and fluid ingredient have multiple field that are also 
different depending on being input or output, but generally follow the same structure as in normal recipes. Each entry on the 
ingredients also has an example of how to use them in recipes.

---
## Example

Example with `"example_category"` as the type, `"item_in"` as a specified item input and `"fluid_out"` as a fluid output.

```json
{
  "type": "example:example_category",
  "item_in": {
    "tag": "minecraft:logs",
    "count": 4
  },
  "fluid_out": {
    "id": "minecraft:water",
    "amount": 2000
  }
}
```

<br>

More examples can be found here: [Example Recipes](/json_jei/neoforge-1.21.1/example/example-datapack/data/example/jei_recipe).