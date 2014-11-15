# Javascript

## Libraries and Scripts

Drupal 8 doesn't load any additional scripts. This also means that by default a library like [jQuery is not included](https://www.drupal.org/node/1541860). This is mostyl due to performance reasons. You have to declare jQuery (or any other core library) as a dependency for your script in order to use it. In the early stages of Drupal 8, this was done using `hook_library_info`. Since this was one of the last remaining hooks in Drupal 8, it got [replaced by a `*.libraries.yml` file](https://www.drupal.org/node/2201089).

> Since Drupal 8 does not support IE8 - and below - and because Javacript has evolved, [you might not need jQuery](http://youmightnotneedjquery.com/). If hovever you do want to use jQuery, make sure to look up some of the [best practices](http://lab.abhinayrathore.com/jquery-standards/) for using jQuery.

Let's add some custom javascript to our theme. Our script will location in the `js` folder inside our theme (`/js/awesome.js`). Next, we create a `*.libraries.yml` file. Let's call this `awesome.libraries.yml` (`{theme-or-module-name}`.libraries.yml) and save it into the root of our theme.

	base:
	  version: 1.x
	  js:
	    js/awesome.js: {}
	  dependencies:
	    - core/drupal
	    - core/jquery
	    - core/jquery.once

> We need `core/drupal` in order to take advantage of the `Drupal.behaviors`. To include the Drupal core version of jQuery, we add `core/jquery`. The final dependency is `core/jquery.once`, a jQuery plugin allowing to only apply a function once to an element.

Back in our `awesome.info.yml` file, we now add the following lines, to include the new declared *library* into our theme.

	libraries:
	  - awesome/base

This includes our the custom javascript and the dependencies into our theme. In this example, both the custom script and the jQuery library are now included in our theme.

`Drupal.behaviors` are still part of javascript in core. Let's open the `awesome.js` and add a little behavior.

	(function ($) {
  	  "use strict"
  	  Drupal.behaviors.awesome = {
        attach: function (context, settings) {
          $('main').once('awesome').append('<p>Hello world</p>');
        }
  	  };
	}(jQuery));

Let's have a quick look at what this does.

The behavior has to have a unique namespace. In the example the namespace is `awesome` (`Drupal.behaviors.awesome`). The `context` variable is the part of the page for which this applies. This is especially useful when working with AJAX.  The `settings` variable is used to pass information from the PHP code to the javascript. Next is some custom code that creates a `p`aragraph-tag, with the text *Hello world*, and appends it to the `main`-tag. Using the `.once('awesome')` will make sure the code only runs once. It adds a `processed`- class to the `main` tag (`<main role="main" class="awesome-processed">`) in order to accomplish this.

Some libraries both have javascript (js) and stylesheets (css). It's possible to include these stylesheets as well. As an example, here's how to include [Picker](http://formstone.it/components/picker) (version 3.1.0) into the `awesome` theme. Most of the parameters are the same, but this time we add a `remote` and `css` tag. Using the `remote` parameter, allows you to define an external link to the library. The `css` tag will include the css file from the library. The level underneath, `theme` is necessary due to the `SMACSS` standard; used for CSS file organisation.

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

## File-closure

All of the javascript code **must** be declared inside a closure wrapping the whole file. This closure **must** be in strict mode.

	(function () {
  	  "use strict";
  	  // Custom javascript
	})();

## "use strict"

The `"use strict"` directive is new in JavaScript 1.8.5 and ignored by previous versions of javascript. The purpose of `"use strict"` is to indicate that the code should be executed in "strict mode". As an example, in *scrict mode*, you cannot use undeclared variables.

## ESHint

> As of Drupal 8, we use ESLint to make sure our JavaScript code is consistent and free from syntax error and leaking variables and that it can be properly minified.

[More on ESLint](https://www.drupal.org/node/1955232)
