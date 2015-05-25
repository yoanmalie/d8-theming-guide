## Twig

Twig is a modern PHP-based compiled templating language. It is part of the Symfony 2 framework and is the default template engine in Drupal 8 ([Read the official change record](https://www.drupal.org/node/1831138)).

All of the `theme_*` functions and PHPTemplate based `*.tpl.php` files have been completely removed and replaced with Twig template files. These template files have a new Twig extension: `*.html.twig`.

When your web page renders, the Twig template engine takes the template file and converts it into a 'compiled' PHP template which it stores in a protected directory in `sites/default/files/php_storage/*` The compilation is done once. Template files are cached for reuse and are recompiled on clearing the Twig cache.

### Coding standards

Twig is a new core programming language and all of the core template files must follow the coding standards. There are both official coding standards from the Twig template engine and coding standards for the usage of Twig in Drupal.

- Generic Twig coding standards: http://twig.sensiolabs.org/doc/coding_standards.html
- Twig in Drupal coding standards: http://drupal.org/node/1823416

### Advantages

Compared to PHPTemplate, Twig offers some major advantages. Especially when it comes to security.

- Twig is more secure, due to the fact that only a number of tags can be used. In the previous PHPTemplate, it was possible for a template file to execute the following code:

		<?php
		  db_query('DROP TABLE {users}');
		?>

  This should of course not be the case. In case you're wondering what it does: it removes the entire `users` table from your database. Not good, right?

- There is now a clear separation between the *logic* and the *view*. This means: no more PHP code inside your template files.
- The syntax is very easy to understand, making the code more readable as well. Also, many IDE's have syntax highlighting for `*.twig` files.
- Template files are reusable, thanks to [Twig includes](http://twig.sensiolabs.org/doc/tags/include.html).
- Debugging is much more easy. First of all, Twig outputs a helpful message with the filename and the line number whenever there is a syntax problem within a template. Secondly, you can turn on a Twig debug function. More on that later.
- Twig is very well documented. Go ahead and [start reading the official documentation here](http://twig.sensiolabs.org/documentation).
- It's not only used in Drupal core, so it's not a Drupaly-thing.

### Disadvantage

- Although the syntax is very easy to read and understand, it's a new syntax you have to learn and get used to before getting started. Once you know the syntax however, you get the advantage of knowing a template engine that can be used outside of Drupal as well. This is due to the fact that Twig is part of the Symfony framework.

***

**Read more**

* [The official Twig documentation from Sensio Labs](http://twig.sensiolabs.org/documentation).
