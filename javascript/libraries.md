## Libraries

## Adding a javascript library

Next, we create a `*.libraries.yml` file. Let's call this `awesome.libraries.yml` (`{theme-or-module-name}`.libraries.yml) and save it into the root of our theme.

  base:
    version: 1.x
    js:
      js/awesome.js: {}
    dependencies:
      - core/drupal
      - core/jquery
      - core/jquery.once

> We need `core/drupal` in order to take advantage of the `Drupal.behaviors`. To include the Drupal core version of jQuery, we add `core/jquery`. The final dependency is `core/jquery.once`, a jQuery plugin allowing to only apply a function once to an element.

Back in our `awesome.info.yml` file, we add the following lines, to include the new declared *library* into our theme.

  libraries:
    - awesome/base

This includes our the custom javascript and the dependencies into our theme. In this example, both the custom script and the jQuery library are now included in our theme.

###

Some libraries both have javascript (js) and stylesheets (css). It's possible to
include these stylesheets as well. As an example, here's how to include
[Picker](http://formstone.it/components/picker) (version 3.1.0) into the
`awesome` theme. Most of the parameters are the same, but this time we add a
`remote` and `css` tag. Using the `remote` parameter, allows you to define an
external link to the library. The `css` tag will include the css file from the
library. The level underneath, `theme` is necessary due to the `SMACSS`
standard; used for CSS file organisation.

    picker:
      version: 3.1.0
      remote: http://formstone.it/components/picker
      js:
        lib/picker/js/jquery.fs.picker.js: {}
      css:
        theme:
          lib/picker/css/jquery.fs.picker.css: {}
      dependencies:
        - core/jquery
