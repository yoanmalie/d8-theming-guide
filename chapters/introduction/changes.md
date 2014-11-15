## Some major changes

Let's kick of with some major changes that you, as a Drupal themer, must be aware of. This is especially useful if you've been involved in Drupal 7 theming in the past.

- The markup in Drupal 8 is now [HTML5](http://buytaert.net/html5-in-drupal-8). New tags like `header`, `nav`, `article` are used in core.

- [WAI-ARIA Roles](https://www.drupal.org/node/1179668) are added. They are a set of roles, states, and properties, which can be applied to markup to provide rich semantics, increasing accessibility and interoperability. Although WAI-ARIA properties were not valid in xhtml 1.0, they are valid in HTML5, and can therefore be applied in the markup of Drupal 8. By using the role attribute with an HTML element, authors can provide more information about the purpose of components on the page.

- `<DIV ID="BAD-PRACTICE">...</DIV>`. Drupal 8 now has 75% less ID's than the Drupal 7 CSS! In other words: **kill all the #ids**!

- [The CSS (File) Structure](https://www.drupal.org/node/1887918) is based on SMACSS & BEM.

- [Drupal is now of the box responsive and mobile ready.](https://groups.drupal.org/mobile/drupal-8)

- [The default settings and config are changed to be fast and safe production values.](https://www.drupal.org/node/2259531)
This is important because in a default Drupal 8 installation, CSS and JS aggregation is enabled. On your local development environment, you "might" want to disable this.

- [A completely new theme/template system: Twig](https://www.drupal.org/node/1831138)
Twig is a completely new theme/template system. This means the `theme_*` functions and PHP-based `*.tpl.php` files have been completely replaced in D8.

- [Drupal 8 does not support browsers that do not support SVG](https://www.drupal.org/node/2298227)
Drupal 8 uses SVG in place of PNG to provide resolution independent icons in the admin UI. No effort is made to cater for browsers that do not support SVG. This includes IE8 and below and Android Browser 2.3 and below.

- Due to the fact that these older browsers are no longer supported, the css in Drupal core is able to move a big step forward. Instead of adding classes like odd, even, first and last; we are now able to use pseudo selectors. [Most first/last/odd/even classes removed in favor of CSS3 pseudo selectors](https://www.drupal.org/node/2178215)

- [An new, empty core theme](https://www.drupal.org/node/2289511)
Read more on *classy*, a new core theme below.

- [CSS classes being moved from preprocess to Twig templates](https://www.drupal.org/node/2325067).

![MortenDK approved](http://mortendk.github.io/drupal8-twig-frankfurt-2014/images/cssfilename-approved.jpg)
