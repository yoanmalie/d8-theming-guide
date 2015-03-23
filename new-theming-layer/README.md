# The new theme layer

Drupal 8 comes with a completely new theme layer. The most significant change of this new layer is of course **Twig**. The old theme layer was a big frustation for front-end developers. Before diving into the new theme layer, let's take a closer look at the *old* one and sum up some of these frustrations and disadvantages.

## The Drupal 7 theme layer

![A simplified wiring guide to the Theme Layer](../img/theme-system.png)

*A simplified wiring guide to the Theme Layer, by **John Albin***

- Drupal-specific template conventions
- With PHPTemplate, anything was possible; such as dropping your entire database from a template file. This made PHPTemplate - and the whole theming layer - very insecure.
- There are three different ways of printing content. Below are three examples. In the first example, a parameter from `an object` is printed. In the second example, a `string` is printed. In the last example, the `$content` variable is a render array. The `render()` function converts this (render) array to HTML markup. Since it returns HTML, it should be used along with print in templates. It's unclear for people unfamiliar to PHP how to display content in a template file.
  From `node.tpl.php`:
  - `<?php print $node->nid; ?> // object`
  - `<?php print $attributes; ?> // string`
  - `<?php print render($content); ?> // array`
- There were too many template files.
- Besides template files, Drupal 7 also used `theme()` function. There were about three times as much `theme()` functions as there were template files. These PHP functions were used to create a string containing html markup based on (more) some complex logic.
- The theme layer was a complex system (of subsystems), almost "impossible" to understand. This wasn't just for people new to Drupal. Even people working on core daily got confused and frustrated about the system. This made Drupal 7 hard to learn.

## The new theme layer

### Removing PHP Template

After a discussion about all the different templating languages, their advantages, disadvantages and their features the decision was made to include the Twig templating engine from the Symfony framework. Drupal could have created it's own, new, PHP based “token" system, but that way Drupal would still be on it's own. By introducing Twig, we are moving from our Drupal island (see blog post in read more). Twig is, just like Symfony, maintained by Sensio Labs. The fact that Drupal adopts Symfony components doesn't necessarily have anything to do with the fact that **Twig** as the new templating language. Twig was chosen because it was the best choice after comparing various templating languages.

> "… We don't have Twig because we have Symfony. It's more that,  we have Twig because it's **AWESOME**"
> *- Scott Reeves, **@Cottser***

Twig makes the Drupal theme layer much more secure. It's impossible to run PHP scripts, make database calls or access the file system. Autoescaping is also enabled by default (more detail in the Twig chapter), a major improvement concerning XSS (Cross-site scripting).

All of the PHPTemplate files were converted to Twig template files.

### Removing the template process layer

**D.O**

- [Remove the process layer (hook_process and hook_process_HOOK)](https://www.drupal.org/node/1843650)
- [The template process layer has been removed](https://www.drupal.org/node/2038981)

> The process layer was only created because we needed a place to flatten complicated data structures such as objects or arrays into strings. In practice, render arrays themselves allow for late rendering via theme function or template file (and can be manipulated in other preprocess functions), and objects can implement __toString methods for printing. There is no longer a need for this whole extra layer of processing before rendering.

@todo: lazy rendering, keep the data structure and render only at the "latest" point

### Converting `theme()` functions to Twig templates

The `theme()` functions are deprecated in Drupal 8 and are all being converted into twig template files.

### Theme suggestion hooks

Main difference: dedicated function to alter the suggestion (instead of preprocess)

**Drupal 7:**

    <?php
    /**
    * Implements hook_preprocess_HOOK() for node templates.
    */
    function MYTHEME_preprocess_node(&$variables) {
      $variables['theme_hook_suggestions'][] = 'node__' . 'my_first_suggestion';
      $variables['theme_hook_suggestions'][] = 'node__' . 'my_second_more_specific_suggestion';
    }

**Drupal 8:**

    <?php
    /**
    * Implements hook_theme_suggestions_HOOK_alter() for node templates.
    */
    function MYTHEME_theme_suggestions_node_alter(array &$suggestions, array $variables) {
      $suggestions[] = 'node__' . 'my_first_suggestion';
      $suggestions[] = 'node__' . 'my_second_suggestion';
    }

***

**Read more**

[Blog post about the future of Drupal](http://www.garfieldtech.com/blog/off-the-island-2013), a blog post by Larry Garfield.
[Drupal 8's new theming layer](https://www.youtube.com/watch?v=Gp3lforZ3ZE), a video interview with Joël Pittet and Scott Reeves.
[The "themer" role is a Drupalism](http://dqxtech.net/blog/2014-10-06/themer-role-drupalism), a blog post by …
[Rethinking Drupal’s Theme/Render Layer](http://john.albin.net/drupal/arrays-of-doom), a blog post by by John Albin.
