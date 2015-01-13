## Javascript

[Introduction]

### jQuery

Drupal 8 doesn't load any additional scripts by default. This also means that a library like [jQuery is not included](https://www.drupal.org/node/1541860) on every page any more. This is mostly due to performance reasons:

You have to declare jQuery (or any other core library) as a dependency for your script in order to use it. In the early stages of Drupal 8, this was done using `hook_library_info`. Since this was one of the last remaining hooks in Drupal 8, it got [replaced by a `*.libraries.yml` file](https://www.drupal.org/node/2201089).

> Since Drupal 8 does not support IE8 - and below - and because Javacript has evolved, [you might not need jQuery](http://youmightnotneedjquery.com/). If however you do want to use jQuery, make sure to look up the [best practices](http://lab.abhinayrathore.com/jquery-standards/) for using jQuery.

#### jQuery and Drupal

Drupal uses jQuery in a no-conflict mode. In jQuery, `$` is an alias for `jQuery`. Other javascript libraries often use `$` as a function or variable name. When using jQuery in a no-conflict mode, this `$` variable is released so other libraries can use this `$` variable.

### Theme function (`Drupal.theme`)

The `Drupal.theme` function [has been simplified](https://www.drupal.org/node/1816980).
Previously it was possible to declare functions in `Drupal.theme.prototype`,
where workaround code made `Drupal.theme()` behave as intended. Instead these
Javascript theme functions are now using `Drupal.theme` directly.

***

**Drupal 7:**

    Drupal.theme.prototype.example = function () {
      var markup = '<p>Hello world!</p>';
      return markup;
    };

    Drupal.theme.prototype.anotherExample = function (title, name) {
      var markup = '<p>Hello ' + title + ' ' + name '!</p>';
      return markup;
    };

    var example = Drupal.theme('example'); // Hello world!
    var another_example = Drupal.theme('anotherExample', 'Mr.', 'Dries'); // Hello Mr. Dries!

**Drupal 8:**

    Drupal.theme.example = function () {
      var markup = '<p>Hello world!</p>';
      return markup;
    };

    Drupal.theme.anotherExample = function (title, name) {
      var markup = '<p>Hello ' + title + ' ' + name '!</p>';
      return markup;
    };

    var example = Drupal.theme('example'); // Hello world!
    var another_example = Drupal.theme('anotherExample', 'Mr.', 'Dries'); // Hello Mr. Dries!

***

#### Declaring several theme functions

Declaring several theme functions can be done using the
[`$.extend()`](http://api.jquery.com/jquery.extend/) pattern. This is a
considered a better approach for declaring serveral functions.

***

    $.extend(Drupal.theme, {
      example: function () { return 'Hello world!'; },
      anotherExample: function (title, name) { return '<p>Hello ' + title + ' ' + name '!</p>'; }
    });

***

### Drupal behaviors (`Drupal.behaviors`)

Let's add some custom javascript to our theme. Our script will location in the
`js` folder inside our theme (`/js/awesome.js`).

`Drupal.behaviors` are still part of javascript in core. Let's open the
`awesome.js` and add a little behavior.

    (function ($) {
      'use strict';
      Drupal.behaviors.awesome = {
        attach: function (context, settings) {
          $('main').once('awesome').append('<p>Hello world</p>');
        }
      };
    }(jQuery));

Let's have a quick look at what this does.

The behavior has to have a unique namespace. In the example the namespace is
`awesome` (`Drupal.behaviors.awesome`). The `context` variable is the part of
the page for which this applies. This is especially useful when working with
AJAX.  The `settings` variable is used to pass information from the PHP code to
the javascript. Next is some custom code that creates a `p`aragraph-tag, with
the text *Hello world*, and appends it to the `main`-tag. Using the
`.once('awesome')` will make sure the code only runs once. It adds a
`processed`- class to the `main` tag
(`<main role="main" class="awesome-processed">`) in order to accomplish this.

### File-closure

All of the javascript code **must** be declared inside a closure wrapping the
whole file. This closure **must** be in strict mode.

    (function () {
        'use strict';
        // Custom javascript
    })();

### 'use strict'

The `"use strict"` directive is new in JavaScript 1.8.5 and ignored by previous
versions of javascript. The purpose of `"use strict"` is to indicate that the
code should be executed in *strict mode*. This *scrict mode* makes it easier to
write more secure javascript and gives error when using a bad syntax. As an
example you cannot use undeclared variables in *script mode*. This will cause an
error.

> The reason for this is that when you use an undeclared variable, this variable
> becomes a new global variable. This can be dangerous when you accidentally
> mistype the name of a variable.
>
>   var message = 'Hello world';
>
>   …
>
>   msg = 'Bye world';
>
> In the example above, a new variable `message` is new declared. Later in the
> script, this `message` should be changed. Instead, the `msg` variable gets
> changed. Since it's not declared, it will be created as new global variable.
> In *strict mode* hover, the example above will cause an error.

### ESHint

> As of Drupal 8, we use ESLint to make sure our JavaScript code is consistent and free from syntax error and leaking variables and that it can be properly minified.

[More on ESLint](https://www.drupal.org/node/1955232)

***

**Read more**

[jQuery.noConflict()](http://api.jquery.com/jquery.noconflict/), from the jQuery API.
