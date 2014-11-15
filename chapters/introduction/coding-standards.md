## Coding standards

It's important to know and follow the Drupal coding standards, especially when you want to get involved into Drupal core (theme) development. It's also useful to follow these standards in your own projects.

There are coding standards for css, javascript and the new Twig template engine:

- [CSS Coding standards](https://www.drupal.org/node/1886770).
- [Javascript Coding standards](https://www.drupal.org/node/172169).
- [Twig Coding standards](https://www.drupal.org/node/1823416).

### SMACSS

Drupal 8 uses the **SMACSS** system to conceptually categorize CSS rules.

1. Base
2. Layout
3. Component (The official **SMACSS** theminoly for this is *modules*. Since *modules* have a different meaning in Drupal, this component was renamed to *component*, to avoid confusion.)
4. State
5. Theme

More information about SMACSS can be found at [SMACSS](https://smacss.com/).

#### SMACSS for Seven

The Seven theme uses these categories to split up the css rules. The Seven theme contains a directory called css. Inside this folder, four more directories live:

- `core/themes/seven/base`
- `core/themes/seven/components`
- `core/themes/seven/layout`
- `core/themes/seven/theme`

[Read more](https://www.drupal.org/node/2321505) about splitting up `style.css` into SMACSS categories.

### BEM

BEM (Block Element Modifier) is a naming convention.

`.block__element--modifier`

- A **block** is an independent entity with its own meaning that represents a piece of interface on a page.
- An **element** is a part of a block, tied to it semantically and functionally. It has no meaning outside of the block it belongs to. Not all blocks have elements.
- **Modifiers** are flags set on blocks or elements; they define properties or states. They may be boolean (for example, visible: true or false) or key-value pairs (size: large, medium, small) — somewhat similar to HTML attributes, but not exactly the same. Multiple modifiers are allowed on a single item if they represent different properties.

Source: [Smashing Magazine](http://www.smashingmagazine.com/2014/07/17/bem-methodology-for-small-projects/)

`buttons.theme.css` (Seven):

`.button {}`, a **block**.
`.button--primary {}`, a **modifier**.

`node.css` (Seven):
`.node__submitted {}`, an **element**.
