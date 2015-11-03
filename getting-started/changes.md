## For those who’ve used Drupal before

Here's a list containing some major changes. This is especially useful if you've been involved in Drupal 7 theming in the past.

- `/core` is the folder where the heart of Drupal lives. This means `/modules` and `/themes` (inside the root of Drupal) now contain *custom* and *contrib* code.

- The markup in Drupal 8 is now [HTML5](http://buytaert.net/html5-in-drupal-8). New tags like `header`, `nav`, `article` are used in core.

- [WAI-ARIA Roles](https://www.drupal.org/node/1179668) are added. They are a set of roles, states, and properties, which can be applied to markup to provide rich semantics, increasing accessibility and interoperability. Although WAI-ARIA properties were not valid in xhtml 1.0, they are valid in HTML5, and can therefore be applied in the markup of Drupal 8. By using the role attribute with an HTML element, authors can provide more information about the purpose of components on the page.

- Drupal 8 now has 75% less ID's than the Drupal 7 CSS!

- [The CSS (File) Structure](https://www.drupal.org/node/1887918) is based on SMACSS & BEM.

- [Drupal is now of the box responsive and mobile ready.](https://groups.drupal.org/mobile/drupal-8)

- [The default settings and config are changed to be fast and safe production values.](https://www.drupal.org/node/2259531)
In a default Drupal 8 installation, CSS and JS aggregation is turned on.

- [A completely new theme/template system: Twig](https://www.drupal.org/node/1831138)
Twig is a completely new theme/template system. This means the `theme_*` functions and PHP-based `*.tpl.php` files have been completely replaced in D8.

- [Drupal 8 does not support browsers that do not support SVG](https://www.drupal.org/node/2298227)
Drupal 8 uses SVG instead of PNG to provide resolution independent icons in the admin UI. No effort is made to cater for browsers that do not support SVG. This includes IE8 and below and Android Browser 2.3 and below.

- Due to the fact that these older browsers are no longer supported, the css in Drupal core is able to move a big step forward. Instead of adding classes like `odd`, `even`, `first` and `last`; CSS3 pseudo selectors are used. [Most first/last/odd/even classes removed in favor of CSS3 pseudo selectors](https://www.drupal.org/node/2178215)

- [An new, empty core theme](https://www.drupal.org/node/2289511). You'll learn more from *classy* later in the documentation.

- [CSS classes being moved from preprocess to Twig templates](https://www.drupal.org/node/2325067).

- …

> A lot more has changed. All of the important change records for themers can be found [here](https://www.drupal.org/list-changes/published/drupal?keywords_description=&to_branch=&version=&created_op=%3E%3D&created%5Bvalue%5D=&created%5Bmin%5D=&created%5Bmax%5D=&impacts%5B%5D=3).
