## Twig

Twig is a modern template engine for PHP. It's part of the Symfony 2 framework. In Drupal 8, Twig is the default template engine ([Read the official change record](https://www.drupal.org/node/1831138).).

All of the `theme_*` functions and PHPTemplate based `*.tpl.php` files have been completely replaced with Twig `.html.twig` template files. The template files now have a new (Twig) extension, `*.html.twig`.

### Coding standards

- Generic Twig coding standards: http://twig.sensiolabs.org/doc/coding_standards.html
- Twig in Drupal coding standards: http://drupal.org/node/1823416

### Advantages

- Twig is more secure, due to the fact that only a number of tags can be used. In the previous PHPTemplate, it was possible for a template file to execute the following code:

		<?php
		  db_query('DROP TABLE {users}');
		?>

  This should of course not be the case. In case you're wondering what it does: it removes the entire `users` table from your database. Not good, right?

- There now is a clear separation between the *logic* and the *view*. This means: no more PHP code inside your template files.
- The syntax is very easy to understand, making the code more readable as well. Also, many IDE's have syntax highlighting for `*.twig` files.
- Template files are reusable, thanks to [Twig includes](http://twig.sensiolabs.org/doc/tags/include.html).
- Debugging is much more easy. First of all, Twig outputs a helpful message with the filename and the line number whenever there is a syntax problem within a template. Secondly, you can turn on a Twig debug function. More on that later.
- Twig is very well documented. Go ahead and [start reading the official documentation here](http://twig.sensiolabs.org/documentation).
- It's not only used in Drupal core, so it's no a Drupaly-thing.

### Disadvantage

- Although the syntax is very easy to read and understand, it's a new syntax you have to learn before getting started.

***

**Read more**

* [The official Twig documentation from Sensio Labs](http://twig.sensiolabs.org/documentation).
