# Category

A jei category requires a few general values to be created and work. The most important value is 
the `uid`. It is used to differentiate categories from one another, thus it has to be **unique**. 
The `uid` is also used inside recipes to set which category the recipe belongs to. The category will
not be loaded, if a category does not contain a `uid`.

| Value           | Explanation                                                                                                                          | Default Value | Example                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------|---------------|------------------------------------------------------------|
| `title`         | The title of the category. This can either be plain text or a translation key.                                                       |               | `"title": "Example category"`                              |
| `icon`          | The item icon that is displayed at the top.                                                                                          |               | `"icon": "minecraft:diamond_block"`                        |
| `background`    | Holds information about the category background. More info below.                                                                    |               | `"background": {...}`                                      |
| `recipe_border` | Controls if jei renders an extra border for each recipe. Should only be set to `false`, if the background contains a visible border. | `true`        | `"recipe_border: true"`                                    |
| `catalysts`     | Holds the items that will be shown at the side of the category, e.g.: smelting has a furnace, crafting a crafting table.             | no side items | `"catalysts": [ "minecraft:diamond", "minecraft:beacon" ]` |
| `recipe_layout` | Holds the layout of the category. More info here: [Recipe Layout](/json_jei/neoforge-1.21.1/entries/recipe_layout.md)                |               |                                                            |
| `rendering`     | Holds extra render components. More info here: [Rendering](/json_jei/neoforge-1.21.1/entries/rendering.md)                           |               |                                                            |

---

## Icon

The icon can be a single item.

```json
{
  "icon": "minecraft:clock"
}
```

<br>

The icon can also be an item with data components.

```json
{
  "icon": {
    "item": "minecraft:clock",
    "components": {
      // data components
    }
  }
}
```

<br>

The icon can also be a texture. The `u` and `v` are the x and y position offset in the texture. By default, the
texture size `256x256`, but can be set with `texture_width` and `texture_height`.

```json
{
  "icon": {
    "texture": "example:textures/gui/icon",
    "u": 0,
    "v": 0,
    "texture_width": 32,
    "texture_height": 32
  }
}
```

---

## Background

| Value     | Explanation                                                  | Example                                        |
|-----------|--------------------------------------------------------------|------------------------------------------------|
| `texture` | The texture that is used as a background.                    | `"texture": "example:textures/gui/background"` |
| `u`       | The x position where the texture starts in the texture file. | `"u": 10`                                      |
| `v`       | The y position where the texture starts in the texture file. | `"v": 50`                                      |
| `width`   | The width of the texture in the texture file.                | `"width": 80`                                  |
| `height`  | The height of the texture in the texture file.               | `"height": 40`                                 |

---

### Full Example

```json
{
  "uid": "example:example_category",
  "title": "Example Category",
  "icon": "minecraft:diamond_block",
  "background": {
    "texture": "example:textures/gui/background",
    "u": 10,
    "y": 50,
    "width": 80,
    "height": 40
  },
  "recipe_border": true,
  "catalysts": [
    "minecraft:diamond",
    "minecraft:beacon"
  ]
}
```