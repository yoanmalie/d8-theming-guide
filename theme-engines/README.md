# Theme engines

Inside the `core/themes` lives a fourth folder (besides `bartik`, `seven` and `stark`), called `engines`. This folder contains the theme engines. In Drupal 8, the default template engine is **Twig**. The default template engine from Drupal 7, PHPTemplate, does still exist. Although it's not recommended to continue using the engine, it might be useful when you're migrating your Drupal 7 site to Drupal 8.

## What is a theme engine?

A theme engines (template engine, template processor or template parser) is a software components that **combines data with templates** from themes and shows the result - the final HTML - to the user.

![Template Engine image from Wikipedia](http://upload.wikimedia.org/wikipedia/commons/thumb/c/c7/TempEngGen015.svg/440px-TempEngGen015.svg.png)
