## The old (Drupal 7) theme layer

The Drupal 7 theming layer had lots of disadvantages:

![A simplified wiring guide to the Theme Layer](../img/theme-system.png)

> *A simplified wiring guide to the Theme Layer, by [John Albin](http://john.albin.net/drupal/arrays-of-doom)*

- Drupal-specific template conventions
- With **PHPTemplate**, anything was possible; even dropping your entire database from a template file. This made PHPTemplate - and the whole theming layer - very insecure.

  `<?php db_query("DROP TABLE {node}"); ?>`

- There are too many different ways to display content in the template. Below are three examples. For people unfamiliar with PHP, it's hard to find out how to display content in a template file.
  From `node.tpl.php`:
  - `<?php print $node->nid; ?> // object`
  - `<?php print $attributes; ?> // string`
  - `<?php print render($content); ?> // array`

> In the first example, a property from an object is printed. In the second example, a string is printed. In the last example, the $content variable is a render array. The render() function converts this (render) array to HTML markup. Since it returns HTML, it should be used along with print in templates.

- There were too many template files.
- Besides template files, Drupal 7 also used `theme()` function. There were even more `theme()` functions than template files. These PHP functions were used to create a string containing html markup based on (more) some complex logic. Syntax highlighting is almost impossible with these functions.
- The theme layer was a complex system, almost *impossible* to understand. This wasn't just for people new to Drupal. Even people working on core daily got confused and frustrated about the system. This makes Drupal 7 hard to learn and is one of the reasons the **learning curve** for new Drupal developers was so high.
