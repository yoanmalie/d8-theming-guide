## File-closure

As part of the Drupal 8 Javascript Coding Standards, all of the javascript code **must** be declared inside a closure wrapping the whole file. This closure **must** be in strict mode.

    (function () {
      'use strict';
      // Custom javascript
    })();
