# Json Ingredients

A custom json ingredient is an ingredient that can be serialized and represented in jei categories. 
In order to create new ingredients for recipes, you have to implement the `JsonIngredient` interface.

---

## Code

Each json ingredient requires a `MapCodec<T>` to be registered and serialized. The map codec
contains all the values about your custom ingredient, like for example the width and height. 
Additionally, it requires a few fields that come from the `JsonIngredient` interface.

<br>

The type is the id the ingredient is registered under and is used to determine what types 
of ingredients a category has when building its recipe layout. This field should **not** be 
serialized inside the map codec, as the codec for all json ingredients already does that.

```java
ResourceLocation type();
```

<br>

The key is used to deserialize the ingredients in recipes. This field should be serialized
inside the map codec.

```java
String key();
```

<br>

Describes the x position inside the jei category. This field should be serialized
inside the map codec and should use the `ExtraCodecs.NON_NEGATIVE_INT` codec to ensure
the ingredient cannot have a negative x position.

```java
int x();
```

<br>

Describes the y position inside the jei category. Like the `x()` position, this should
also be serialized in the map codec with the `ExtraCodecs.NON_NEGATIVE_INT` codec.

```java
int y();
```

<br>

The `place(...)` method is called for each recipe to place the ingredients into the slot. 
The `IRecipeSlotBuilder` is set up so that it already knows the x and y position as well
as if the slot is an input or an output.

The `recipe` field holds the information about the contents of the recipe. It is gathered
using the `key()` of the ingredient. If the recipe does not contain that key and `placeNullable()`
returns `false` this method will **not** be called, otherwise the field can, but does not have to be `null`.

```java
void place(IRecipeSlotBuilder builder, @UnknownNullability JsonElement recipe, boolean isInput);
```

<br>

Describes if an ingredient can be placed even if the `recipe` field in the `place(...)` method is `null`.
If this method returns `false` the `place(...)` method will not be called.

```java
default boolean placeNullable() {
    return true;
}
```

<br>

Lastly each custom ingredient needs to be registered with the `JsonRegisterEvent`. The `type` field has to 
match the `type()` method as its used as a lookup and the `codec` is the map codec with all values of the ingredient.

```java
JsonRegisterEvent#registerIngredient(ResourceLocation type, MapCodec<? extends JsonIngredient> codec);
```

---

### Example

A json ingredient for an `ExampleIngredient`:

```java
public record JsonExample(String key, int x, int y, int width, int height) implements JsonIngredient {
    public static final MapCodec<JsonExample> CODEC = RecordCodecBuilder.mapCodec(instance -> instance.group(
            Codec.STRING.fieldOf("key").forGetter(JsonExample::key),
            ExtraCodecs.NON_NEGATIVE_INT.optionalFieldOf("x", 0).forGetter(JsonExample::x),
            ExtraCodecs.NON_NEGATIVE_INT.optionalFieldOf("y", 0).forGetter(JsonExample::y),
            ExtraCodecs.POSITIVE_INT.optionalFieldOf("width", 1).forGetter(JsonExample::width),
            ExtraCodecs.POSITIVE_INT.optionalFieldOf("height", 1).forGetter(JsonExample::height)
    ).apply(instance, JsonExample::new));

    @Override
    public ResourceLocation type() {
        return ResourceLocation.fromNamespaceAndPath("example", "example_ingredient");
    }

    @Override
    public void place(IRecipeSlotBuilder builder, JsonElement element, boolean isInput) {
        JsonJei.parseCodec(ExampleIngredient.CODEC, element, ingredient -> builder
                .addIngredient(ExampleIngredient.TYPE, ingredient)
        );
    }
}
```

Lastly registering:

```java
@SubscribeEvent
private static void register(JsonRegisterEvent event) {
    event.registerIngredient(
            ResourceLocation.fromNamespaceAndPath("example", "example_ingredient"),
            JsonExample.CODEC
    );
}
```

---

## Rendered json ingredients

The `JsonRenderedIngredient` interface is an extension to the normal json ingredients allowing to render
extra things.

The interface provides the extra method `render(...)` to render things like a background or an overlay.

```java
void render(GuiGraphics guiGraphics, double mouseX, double mouseY);
```

**Note**: This will be used to style all ingredients used in a category. Individual custom
ingredients should be styled with JEIs [`IIngredientRenderer<T>`](https://github.com/mezz/JustEnoughItems/blob/1.21.1/CommonApi/src/main/java/mezz/jei/api/ingredients/IIngredientRenderer.java) instead.

### Example

This renders the background and overlay for fluid ingredients, when the required values in
the json are set to `true`.

```java
@Override
public void render(GuiGraphics guiGraphics, double mouseX, double mouseY) {
    if (hasBackground) {
        guiGraphics.blitSprite(JsonJei.id("tank_background"), x - 1, y - 1, width + 2, height + 2);
    }

    if (hasOverlay) {
        JsonJei.renderOver(guiGraphics, g -> g.blitSprite(JsonJei.id("tank_overlay"), x - 1, y - 1, Math.min(width, 16) + 2, height + 2));
    }
}
```