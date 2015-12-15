## The heart of Drupal

`/core` is the folder where the heart of Drupal lives. This means `/modules` and `/themes` (inside the root of Drupal) now contain *custom* and *contrib* code. The core themes live inside `/core/themes`.

## HTML5

The markup of Drupal 8 is written using [HTML5](http://buytaert.net/html5-in-drupal-8). New tags like `header`, `nav`, `article` are used in core.

**Read more**:
- [The Drupal HTML5 Group](https://groups.drupal.org/html5)

## Accessibility

[WAI-ARIA Roles](https://www.drupal.org/node/1179668) are added. They are a set of roles, states, and properties, which can be applied to markup to provide rich semantics, increasing accessibility and interoperability. Although WAI-ARIA properties were not valid in xhtml 1.0, they are valid in HTML5, and can therefore be applied in the markup of Drupal 8. By using the role attribute with an HTML element, authors can provide more information about the purpose of components on the page.

## Responsive

Drupal is now out-of-the-box responsive and mobile ready.

**Read more**:
- [Drupal is now out-of-the-box responsive and mobile ready.](https://groups.drupal.org/mobile/drupal-8)

## Browser support

Drupal 8 uses SVG instead of PNG to provide resolution independent icons in the admin UI. No effort is made to cater for browsers that do not support SVG. This includes **IE8 and below** and **Android Browser 2.3 and below**.

Due to the fact that these older browsers are no longer supported, the css in Drupal core is able to move a big step forward. Instead of adding classes like `odd`, `even`, `first` and `last`; CSS3 pseudo selectors are used to target these items.

**Read more**:
- [Drupal 8 does not support browsers that do not support SVG](https://www.drupal.org/node/2298227)
- [Most first/last/odd/even classes removed in favor of CSS3 pseudo selectors](https://www.drupal.org/node/2178215)

***

**Read more**

> A lot more has changed if you're familiar with Drupal 7. All of the important change records for themers can be found [here](https://www.drupal.org/list-changes/published/drupal?keywords_description=&to_branch=&version=&created_op=%3E%3D&created%5Bvalue%5D=&created%5Bmin%5D=&created%5Bmax%5D=&impacts%5B%5D=3).
