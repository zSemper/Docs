# Json Render Components

Render components are extra things that can be rendered onto the jei category,
like text or textures. Like json ingredients, to create a new json render component
you need to implement the `JsonRenderComponent` interface.

---

## Code

Each render component requires a `MapCodec<T>` to be registered and serialized.
Additionally, it requires a few fields that come from the `JsonRenderComponent` interface.

<br>

The type is the id the render component is registered under. This field should **not**
be serialized in the map codec.

```java
ResourceLocation type();
```

<br>

The key is used to deserialize the render component overrides in a recipe. This is also
used as a lookup for reference values of render components. This field should be serialized in the map codec.

```java
String key();
```

<br>

An optional field for the default values of reference values. This field should be serialized in
the map codec with `optionalFieldOf(...)`.

```java
Optional<JsonElement> values();
```

<br>

The `render(...)` method is called to render the actual component. The `override` field holds the overridden render
component from the recipe, or `null` if not present. The JsonObject `recipeValues` holds the recipe specific 
values to the reference values of the components.

```java
void render(GuiGraphics guiGraphics, @Nullable JsonElement override, JsonObject recipeValues, double mouseX, double mouseY);
```

To properly decode reference values `JsonRenderComponent` provides a helper method:

```java
default /*final*/ <T> T decode(Codec<T> codec, ReferenceValue<T> value, JsonElement recipeValues);
```

The `codec` field is the codec the reference value has. The `value` field is the reference value and 
`recipeValues` is the `JsonObject` that holds the values to all reference values.

<br>

And like json ingredients, json render components also need to be registered with the `JsonRegisterEvent`. 
The `type` matches the `type()` method and the `codec` is the map codec with all the values.

```java
JsonRegisterEvent#registerRenderComponent(ResourceLocation type, MapCodec<? extends JsonRenderComponent> codec);
```

---

### Example

Implementation of the sprite render component:

```java
public record SpriteRenderComponent(
        String key,
        ResourceLocation texture,
        ReferenceValue<Integer> x,
        ReferenceValue<Integer> y,
        ReferenceValue<Integer> width,
        ReferenceValue<Integer> height,
        Optional<JsonElement> values
) implements JsonRenderComponent {
    public static final MapCodec<SpriteRenderComponent> CODEC = RecordCodecBuilder.mapCodec(instance -> instance.group(
            Codec.STRING.fieldOf("key").forGetter(SpriteRenderComponent::key),
            ResourceLocation.CODEC.fieldOf("texture").forGetter(SpriteRenderComponent::texture),
            ReferenceCodecs.NON_NEGATIVE_INT_CODEC.optionalFieldOf("x", new ReferenceValue.Literal<>(0)).forGetter(SpriteRenderComponent::x),
            ReferenceCodecs.NON_NEGATIVE_INT_CODEC.optionalFieldOf("y", new ReferenceValue.Literal<>(0)).forGetter(SpriteRenderComponent::y),
            ReferenceCodecs.POSITIVE_INT_CODEC.optionalFieldOf("width", new ReferenceValue.Literal<>(1)).forGetter(SpriteRenderComponent::width),
            ReferenceCodecs.POSITIVE_INT_CODEC.optionalFieldOf("height", new ReferenceValue.Literal<>(1)).forGetter(SpriteRenderComponent::height),
            ExtraCodecs.JSON.optionalFieldOf("values").forGetter(SpriteRenderComponent::values)
    ).apply(instance, SpriteRenderComponent::new));

    @Override
    public ResourceLocation type() {
        return JsonJei.id("sprite");
    }

    @Override
    public void render(GuiGraphics guiGraphics, @Nullable JsonElement override, JsonObject recipeValues, double mouseX, double mouseY) {
        if (element != null) {
            JsonJei.parseCodec(CODEC.codec(), override, component -> component.render(guiGraphics, null, recipeValues, mouseX, mouseY));
            return;
        }

        int dx = decode(Codec.INT, "x", x, recipeValues);
        int dy = decode(Codec.INT, "y", y, recipeValues);
        int dWidth = decode(Codec.INT, "width", width, recipeValues);
        int dHeight = decode(Codec.INT, "height", height, recipeValues);

        guiGraphics.blitSprite(JsonJei.validateTexture(texture), dx, dy, dWidth, dHeight);
    }
}
```

---

## Reference Values

Reference values are values that are either a key that points to a value, or the value itself.
They are serialized and deserialized by reference codecs.

To create your own reference codec use the `create(...)` method in the `ReferenceCodecs` class.
The `baseCodec` field, is the codec for the actual value and the `referenceType` represents
the character in the json: `$([referenceType]:[key])`.

```java
static <T> Codec<ReferenceValue<T>> create(Codec<T> baseCodec, char referenceType);
```

<br>

To decode the references into actual values. you can use the `resolve(...)` method. The provided string
in the function is the key of the reference value.

```java
default /*final*/ T resolve(Function<String, T> lookup);
```

<br>

JsonJei also provides a handful of existing reference codecs that can be found in `ReferenceCodecs`:
- `INT_CODEC`
- `DOUBLE_CODEC`
- `BOOLEAN_CODEC`
- `STRING_CODEC`
- `POSITIVE_INT_CODEC`
- `NON_NEGATIVE_INT_CODEC`
