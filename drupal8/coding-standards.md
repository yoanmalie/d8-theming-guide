## Coding standards

It's important to know and follow the Drupal coding standards, especially when you want to get involved into Drupal core development. It's also useful to follow these coding standards in your own projects.

There are coding standards for **css**, **javascript** and the new **Twig** template engine:

- [CSS Coding standards](https://www.drupal.org/node/1886770).
- [Javascript Coding standards](https://www.drupal.org/node/172169).
- [Twig Coding standards](https://www.drupal.org/node/1823416).

### SMACSS

Drupal 8 uses the **SMACSS** system to conceptually categorize CSS rules.

1. Base
2. Layout
3. Component (The official **SMACSS** theminoly for this is *modules*. Since *modules* have a different meaning in Drupal, this category was renamed to *component* to avoid confusion.)
4. State
5. Theme (Sometimes also called **skin**, again since avoid the confusion with Drupal *themes*.)

More information about SMACSS can be found on the [SMACSS](https://smacss.com/) website.

![MortenDK approved](../img/mortendk.jpg)

#### SMACSS for Seven

The Seven theme uses these categories to split up the css rules. The Seven theme contains a directory called `css`. Inside this folder, four more directories live:

- `core/themes/seven/base`
- `core/themes/seven/components`
- `core/themes/seven/layout`
- `core/themes/seven/theme`

These folder contain the stylesheet (`.css` files) for each corresponding category.

[Read more](https://www.drupal.org/node/2321505) about splitting up `style.css` into SMACSS categories.

### BEM

BEM (Block Element Modifier) is a naming convention.

@Todo: Might not be relevant any more, doesn't seem to be a part of the coding standards any more.

`.block__element--modifier`

- A **block** is an independent entity with its own meaning that represents a piece of interface on a page.
- An **element** is a part of a block, tied to it semantically and functionally. It has no meaning outside of the block it belongs to. Not all blocks have elements.
- **Modifiers** are flags set on blocks or elements; they define properties or states. They may be boolean (for example, visible: true or false) or key-value pairs (size: large, medium, small) — somewhat similar to HTML attributes, but not exactly the same. Multiple modifiers are allowed on a single item if they represent different properties.

Source: [Smashing Magazine](http://www.smashingmagazine.com/2014/07/17/bem-methodology-for-small-projects/)

`buttons.theme.css (Seven)`:

- `.button {}`, a **block**.
- `.button--primary {}`, a **modifier**.

`node.css (Seven)`:

- `.node__submitted {}`, an **element**.

***

**Read more**

* [Organize Your Styles - An Introduction to SMACSS](https://www.acquia.com/blog/organize-your-styles-introduction-smacss), a blog post by Acquia.
* [BEM and SMACSS: Advice From Developers Who’ve Been There](http://www.sitepoint.com/bem-smacss-advice-from-developers/), a blog post by New Relic.
