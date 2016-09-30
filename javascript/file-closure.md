## File-closure

As part of the Drupal 8 Javascript Coding Standards, all of the javascript code **must** be declared inside a closure wrapping the whole file. This closure **must** be in strict mode.

This method (or better function) is also called an IIFE (Immediately-Invoked Function Expression) and is executed immediately after it’s created.

    (function () {
      'use strict';
      // Custom javascript
    })();

