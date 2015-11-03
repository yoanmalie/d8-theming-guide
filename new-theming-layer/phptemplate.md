## PHPTemplate

**PHPTemplate** was the default template engine for Drupal 7. It was written by [Adrian Rossouw](https://www.drupal.org/user/1337/view).

The engine uses individual template files (`*.tpl.php` extension, such as `example.tpl.php`), to theme Drupal's `theme_` functions, such as `theme_pager()`

An extract from **node.tpl.php** in Drupal 7:

    <div id="node-<?php print $node->nid; ?>" class="<?php print $classes; ?> clearfix"<?php print $attributes; ?>>

      <?php print $user_picture; ?>

      <?php print render($title_prefix); ?>
      <?php if (!$page): ?>
        <h2<?php print $title_attributes; ?>><a href="<?php print $node_url; ?>"><?php print $title; ?></a></h2>
      <?php endif; ?>
      <?php print render($title_suffix); ?>
      …

### Removing PHP Template

After a discussion about the advantages, disadvantages and features of various templating languages, the decision was made to include the Twig templating engine from the Symfony framework. Drupal could have created its own, new, PHP based “token" system, but that way Drupal would still be on its own. By introducing Twig, Drupal is moving away from the Drupal island it's been on for many years. Twig is, just like Symfony, maintained by Sensio Labs. The fact that Drupal adopts Symfony components doesn't necessarily have anything to do with the adoption of **Twig** as the new templating language. Twig was chosen because it was the best choice after comparing various templating languages.

> "… We don't have Twig because we have Symfony. It's more that,  we have Twig because it's **AWESOME**"

*- Scott Reeves, @Cottser*

Twig makes the Drupal theme layer faster and more secure. It's impossible to run PHP scripts, make database calls or access the file system. Autoescaping is also enabled by default (more detail in the Twig chapter), a major improvement concerning XSS (Cross-site scripting).

> In order to use the raw data (not escaped), you have to use the Twig `|raw` filter. In the Twig chapter, more information can be found.

All of the PHPTemplate files (`*.tpl.php`) were converted to Twig template files (`*.html.twig`).
