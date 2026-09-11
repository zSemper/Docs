# Texture Render Component

The texture component is used to render extra static or animated textures, like progress arrows, onto the recipes.
The texture file has to be `256x256` pixel in size to properly render.

To allow a texture to be animated the `"time"` has to be set above `0`.

| Value             | Explanation                                                                                                | Default Value | Reference Key | Example                                      |
|-------------------|------------------------------------------------------------------------------------------------------------|---------------|---------------|----------------------------------------------|
| `texture`         | The actual texture that is rendered.                                                                       |               |               | `"texture": "example:textures/gui/progress"` |
| `width`           | The width of the texture in the texture file.                                                              | `0`           | `$(i:[key])`  | `"width": 32`                                |
| `height`          | The height of the texture in the texture file.                                                             | `0`           | `$(i:[key])`  | `"height": 32`                               |
| `u`               | The x position where the texture starts in the texture file.                                               | `0`           | `$(i:[key])`  | `"u": 16`                                    |
| `v`               | The y position where the texture starts in the texture file.                                               | `0`           | `$(i:[key])`  | `"v": 16`                                    |
| `x`               | The x position where the texture is rendered in the recipe.                                                | `0`           | `$(i:[key])`  | `"x": 64`                                    |
| `y`               | The y position where the texture is rendered in the recipe.                                                | `0`           | `$(i:[key])`  | `"x": 64`                                    |
| `time`            | Controls if the texture is animated or static. The time in ticks the texture needs to finished one cycle.  | `0`           | `$(i:[key])`  | `"time": 100`                                |
| `start_direction` | Controls where the animated texture starts from. Possible values: `"left"`, `"right"`, `"top"`, `"bottom"` | `"left"`      | `$(s:[key])`  | `"start_direction": "right"`                 |
| `inverted`        | If true, texture will render full and disappear over time.                                                 | `false`       | `$(b:[key])`  | `"inverted": true`                           |

## Example

```json
{
  "type": "json_jei:texture",
  "key": "texture_key",
  "texture": "example:textures/gui/progress",
  "width": 32,
  "height": 32,
  "u": 16,
  "v": 16,
  "x": 64,
  "y": 64,
  "time": 100,
  "start_direction": "right",
  "inverted": true
}
```