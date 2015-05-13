# Theme engines

Inside the `core/themes` lives a fourth folder (besides `bartik`, `seven`, `stark` and `classy`), called `engines`. This folder contains the theme engines. In Drupal 8, the default template engine is **Twig**. The default template engine from Drupal 7 hoverever, PHPTemplate, does still live in there. Although it's not recommended to continue using the engine, it might be useful when you're migrating your Drupal 7 sites to Drupal 8. Bare in mind that Twig has a lot more to offer and is more secure than PHPTemplate.

## What is a theme engine?

A theme engine (also called template engine, template processor or template parser) is a software components that **combines data with templates** from themes and shows the result - the final HTML - to the user.

![Template Engine](https://raw.githubusercontent.com/sqndr/d8-theming-guide/master/img/template-engine.png)

### PHPTemplate

**PHPTemplate** was the default template engine for Drupal 7. It was written by [Adrian Rossouw](https://www.drupal.org/user/1337/view).

The engine uses individual template files (`*.tpl.php` extension, such as `example.tpl.php`), to theme Drupal's `theme_` functions (`theme_example()`).
