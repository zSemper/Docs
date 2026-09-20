# Time Render Component

The time component is a convenience render component displaying a `16x16` icon and a given time 
in a tooltip as `[minutes]m [seconds]s`.

| Value  | Explanation                          | Default Value               | Reference Key | Example       |
|--------|--------------------------------------|-----------------------------|---------------|---------------|
| `icon` | The displayed icon in the category   | `"item": "minecraft:clock"` |               | Below         |
| `x`    | The x position of the time component | `0`                         | `$(i:[key])`  | `"x": 30`     |
| `y`    | The y position of the time component | `0`                         | `$(i:[key])`  | `"y": 50`     |
| `time` | The time                             |                             | `$(i:[key])`  | `"time": 100` |

## Example

```json
{
  "type": "json_jei:time",
  "key": "time_key",
  "icon": "minecraft:clock",
  "x": 30,
  "y": 50,
  "time": 100
}
```

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
texture size `256x256`, but can be set with `texture_width` and `texture_height`. The width and height of the icon
is always `16x16`.

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