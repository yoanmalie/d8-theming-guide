## Twig debug

A new feature in Drupal core is the **Twig debug** tool. It allows developers to trace from which template files certain markup comes. To enable Twig Debugging, set the `debug` parameter in the `twig.config ` to `true`.

![](../img/twig-debug-services.png)

**sites/default/services.yml**:

    parameters:
      twig.config:
        debug: true # originally false

When opening the web console, HTML comments are added:

    <!-- FILE NAME SUGGESTIONS:
       * html--front.html.twig
       * html--.html.twig
       x html.html.twig
    -->
    <!-- BEGIN OUTPUT from 'core/modules/system/templates/html.html.twig' -->

![](../img/twig-debug-example.png)

> A system like this has been backported to **Drupal 7**. It can be activated by adding `$conf['theme_debug'] = TRUE;` inside `settings.php`

### Theme debug suggestions

The files with **(\*)** are theme hook suggestions, and can be used to override the template file in more specific and less generic use cases. The file marked with **(x)** is template file that is currently being used to print the markup. The comments end with the file that is currently being using to print the markup.

    <!-- FILE NAME SUGGESTIONS:
       * html--front.html.twig
       * html--.html.twig
       x html.html.twig
    -->
    <!-- BEGIN OUTPUT from 'core/modules/system/templates/html.html.twig' -->

### Debug a variable

To print all the available variables (in a template file), the `dump()`-function can be used. To print the content of a specific variable you have to pass the name of the variable as a parameter to the function.

> **Note:** When using the `dump()`, you might stumble upon a white screen of death. The command is recursively traversing and printing all the variables, which consumes too much memory. Instead, try using `{{ dump(_context|keys) }}`, which will only print all the available keys.

Print *all* available variables:

    {{ dump() }}

> **Note:** This is the equivalent of `dump(_context)`, see below.

Print content of `$foo` variable:

    {{ dump(foo) }}

Print content of `$foo` and `$bar` variables:

    {{ dump(foo, bar) }}

There are two **global variables** in all Twig templates:

* `_context`, which contains all variables that are passed to the template file. When using `dump()` without passing in a variable, the `_context` will be printed.

* `_charset`, which references the (current) charset.

### Using Devel and Kint

The `dump()` can be useful to debug a single variable, but when dumping all the variables the output can be overwhelming. This is where the [**Devel** module](https://www.drupal.org/project/devel) jumps in. This *contrib* module contains several submodules. One of them is **Kint**, a tool to present debugging data in a nice UI (instead of long strings on the screen).

        # Download the Devel module
        drush dl devel
        # Enable the Devel & Kint module
        drush en devel kint

Once enabled, all the `dump()` commands can be replace with `kint()` - or `kint(foo)` - for better debugging.

---

**Read more**

* [Add Kint functionality to Twig templates](https://www.drupal.org/node/2218949)
* [Discovering and Inspecting Variables in Twig Templates](https://www.drupal.org/node/1906780)
* [Debugging compiled Twig templates](https://drupal.org/node/1903374)
