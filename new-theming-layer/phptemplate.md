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
