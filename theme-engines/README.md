# Theme engines

Inside the `core/themes` lives a fourth folder (besides `bartik`, `seven`, `stark` and `classy`), called `engines`. This folder contains the theme engines. In Drupal 8, the default template engine is **Twig**. The default template engine from Drupal 7 hoverever, PHPTemplate, does still live in there. Although it's not recommended to continue using the engine, it might be useful when you're migrating your Drupal 7 sites to Drupal 8. Bare in mind that Twig has a lot more to offer and is more secure than PHPTemplate.

## What is a theme engine?

A theme engine (also called template engine, template processor or template parser) is a software components that **combines data with templates** from themes and shows the result - the final HTML - to the user.

![Template Engine](https://raw.githubusercontent.com/sqndr/d8-theming-guide/master/img/template-engine.png)

## `theme_`-functions

This section is dedicated to all people who have been dealing with `theme_`-functions in Drupal 7. All of these function are gone and have been replaced with template files. 
