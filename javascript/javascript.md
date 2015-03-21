## Javascript

[Introduction]

### jQuery

Drupal 8 doesn't load any additional scripts by default. This means that [jQuery is not included](https://www.drupal.org/node/1541860) on every page any more. This is mostly due to performance reasons: you don't need jQuery on every page, so Drupal should only load it when needed. In order to use jQuery, you have to declare jQuery (or any other core library) as a dependency for your script. In the early stages of Drupal 8, this was done using `hook_library_info`. Since this was one of the last remaining hooks in Drupal 8, it got [replaced by a `*.libraries.yml` file](https://www.drupal.org/node/2201089).

> Since Drupal 8 does not support IE8 - and below - and because Javacript has evolved, [you might not need jQuery](http://youmightnotneedjquery.com/). If however you do want to use jQuery, make sure to look up the [best practices](http://lab.abhinayrathore.com/jquery-standards/) for using jQuery.

#### jQuery and Drupal

Drupal uses jQuery in a no-conflict mode. In jQuery, `$` is an alias for `jQuery`. Other javascript libraries often use `$` as a function or variable name. When using jQuery in a no-conflict mode, this `$` variable is released so other libraries can use this `$` variable.

### Theme function (`Drupal.theme`)

`Drupal.theme` is the client-side counterpart of the server-side `theme()`-function. Most of the server-side `theme()` function has been removed in Drupal 8. The client-side function however remains part of the Javascript API. All markup (defined in Javascript) should go through these theme functions.

The beautify of this system is that it allows the reuse of theme functions as templates and the override of these functions in themes. A module can define a theme functions; a theme thats wants to change the markup can override the function to define it's own template.

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

Drupal behaviors (`Drupal.behaviors`) are still part of javascript in core. These behaviors will be executed on every request, including AJAX requests.

Below is an example of a Drupal Javascript Behavior.

    (function ($) {
      'use strict';
      Drupal.behaviors.awesome = {
        attach: function(context, settings) {
          $('main').once('awesome').append('<p>Hello world</p>');
        }
      };
    }(jQuery));

Let's have a quick look at what this does.

- **namespace**:
A Drupal behavior has to have a unique namespace. In this example, the namespace is `awesome` (`Drupal.behaviors.awesome`).

- **attach**:
Contains the actual function that should be executed.

- **context**:
The `context` variable is the part of the page for which this applies. On a page load, this will be the entire document. On a AJAX request however, the `context` variable will only contain all the newly loaded elements.

- **settings**:
The `settings` variable is used to pass information from the PHP code to the javascript (`core/drupalSettings`).

- **once**:
Using the `.once('awesome')` will make sure the code only runs once. It adds a `processed`- class to the `main` tag (`<main role="main" class="awesome-processed">`) in order to accomplish this (`core/jquery.once`).


    (function ($) {
        'use strict';
        Drupal.behaviors.awesome = {
          attach: function(context, settings) {
          },
          detach: function (context, settings, trigger) {
          }
        };
      }(jQuery));

- **detach**:
Alongside `attach` lives `detach`, which can be used to detach registered behaviors from a page element. Besides from a `context` and `settings`, it also expects a `trigger`. The `trigger` is a string containing the causing of the behavior to be detached. Possible causings are:

  - *unload*: (default) The context element is being removed from the DOM.
  - *move*: The element is about to be moved within the DOM (for example,
  during a tabledrag row swap). After the move is completed,
  Drupal.attachBehaviors() is called, so that the behavior can undo
  whatever it did in response to the move. Many behaviors won't need to
  do anything simply in response to the element being moved, but because
  IFRAME elements reload their "src" when being moved within the DOM,
  behaviors bound to IFRAME elements (like WYSIWYG editors) may need to
  take some action.
  - *serialize*: When an Ajax form is submitted, this is called with the
  form as the context. This provides every behavior within the form an
  opportunity to ensure that the field elements have correct content
  in them before the form is serialized. The canonical use-case is so
  that WYSIWYG editors can update the hidden textarea to which they are
  bound.

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
