# Json Jei

A mod about adding custom jei categories and recipes via data- and resource-packs. 
Useful for modpack creator to show custom functionalities or recipes inside jei.

---

## Categories

Jei uses categories to show different recipes. To create a category the json file must
be placed under the specific path: `/data/[namespace]/jei_category/`.

The json for a category is made up of three different parts:

1. [Category](/json_jei/neoforge-1.21.1/entries/category.md)
2. [Recipe Layout](/json_jei/neoforge-1.21.1/entries/recipe_layout.md)
3. [Rendering](/json_jei/neoforge-1.21.1/entries/rendering.md)

**Note**: Categories cannot be reloaded, unlike other things under the `/data/` path, using `/reload` and
require a full game restart for changes to be applied.

## Recipes

Recipes for these custom categories are placed under the `/data/[namespace]/jei_recipe/` path to be 
registered by the mod.

[Recipes](/json_jei/neoforge-1.21.1/entries/recipes.md)

Like normal recipes, custom recipes can also be placed in subfolder inside the `jei_recipe` folder and 
can be reloaded using the `/reload` command.

---
## Example

Under `json_jei/neoforge-1.21.1/example` is a working data- and resource-pack that can be used as reference alongside the documentation.

[Example](/json_jei/neoforge-1.21.1/example)

---
## Feature request

Feature requests are always welcome to expand this mod.
