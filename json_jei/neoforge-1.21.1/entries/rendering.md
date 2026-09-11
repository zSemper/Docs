# Rendering

Render components allow to add extra things to jei categories. They are not required, but can make categories
more lively and understandable.

Each render component is put in the `"rendering": [...]` field.
They require a `"type"` and a `"key"` field, which are similar to ingredients in the recipe layout. 

The `"type"` field describes which type the render component is being rendered.
Json Jei provides six different render components:

| Render Component                                                                    | Type                         |
|-------------------------------------------------------------------------------------|------------------------------|
| [Text Component](/json_jei/neoforge-1.21.1/entries/render_components/text.md)       | `"type": "json_jei:text"`    |
| [Tooltip Component](/json_jei/neoforge-1.21.1/entries/render_components/tooltip.md) | `"type": "json_jei:tooltip"` |
| [Texture Component](/json_jei/neoforge-1.21.1/entries/render_components/texture.md) | `"type": "json_jei:texture"` |
| [Sprite Component](/json_jei/neoforge-1.21.1/entries/render_components/sprite.md)   | `"type": "json_jei:sprite"`  |
| [Item Component](/json_jei/neoforge-1.21.1/entries/render_components/item.md)       | `"type": "json_jei:item"`    |
| [Time Component](/json_jei/neoforge-1.21.1/entries/render_components/time.md)       | `"type": "json_jei:time"`    |

New render components can also be added: [Custom Render Components](/json_jei/neoforge-1.21.1/entries/render_components/custom_render_component.md) 

<br>

The `"key"` field is used as a lookup for reference values and overriding whole render components inside recipes.
Each `"key"` has to be **unique**, there should be no two render components and ingredients that share the same key.

---

## Reference Values

Reference values are a way to change values of render components in individual recipes. Most values of render components
can be reference values. Reference values follow the pattern of `"s([type]:[key])"`, where the type describes the type of
the value, like `i` is an integer or `b` is a boolean, and the key being the lookup for the actual value.

Each render component can have a `values` field where the default reference values can be set.

```json
{
  "key": "custom_render",
  "x": "$(i:custom_x_position)",
  "y": "$(i:custom_y_position)",
  "values": {
    "custom_x_position": 10
  }
}
```

If a render component does not set a default value it has to be set in each recipe. To set them, recipes require an
extra field `values`, in it the key of the render component is used to set the value. If a recipe does not have a value
the game crashes with an error similar to this: `"com.google.gson.JsonParseException: Expected key 'time' is recipe 'example:burning/coal', but it's missing"`.

```json
{
  "values": {
    "custom_render": {
      "custom_x_position": 20,
      "custom_y_position": 20
    }
  }
}
```

---

## Overriding render components

Recipes an override whole components from the same `"type"` by using the set `"key"`. When a render component
gets overriding all required values, except the `"key"` value, have to be set in the recipe.

For example a category has a render component with the key set to `"key": "render_key"`, than a recipe
can override that:

```json
{
  "render_key": {
    // new render component values
  }
}
```
