# Sprite Render Component

Sprites are similar to textures, but can be resized and cannot be animated. A sprite texture uses the full
size of the texture file. 

| Value     | Explanation                       | Default Value | Reference Key | Example                                    |
|-----------|-----------------------------------|---------------|---------------|--------------------------------------------|
| `texture` | The texture sprite to render      |               |               | `"texture": "example:textures/gui/sprite"` |
| `x`       | The x position of the texture     | `0`           | `$(i:[key])`  | `"x": 15`                                  |
| `y`       | The y position of the texture     | `0`           | `$(i:[key])`  | `"y": 40`                                  |
| `width`   | The width of the rendered sprite  | `1`           | `$(i:[key])`  | `"width": 16`                              |
| `height`  | The height of the rendered sprite | `1`           | `$(i:[key])`  | `"height": 16`                             |

## Example

```json
{
  "type": "json_jei:sprite",
  "key": "sprite_key",
  "texture": "example:textures/gui/sprite",
  "x": 15,
  "y": 40,
  "width": 16,
  "height": 16
}
```