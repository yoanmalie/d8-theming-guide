## Twig debug

An **awesome** new feature from the Twig engine is the debug tool. It allows you to trace where the template file comes from. To enable Twig Debugging, all you have to do is set the `debug` variable in the `twig.config ` to `true`.

    `sites/default/services.yml`:
    ---

    parameters:
      twig.config:
        debug: true # originally false

> A system like this has been backported to **Drupal 7**. It can be activated by adding `$conf['theme_debug'] = TRUE;` inside `settings.php`

### Finding a variable.

To print all the available variables (in a template file) the `dump()`-function can be used. To print the content of a specific variable you have to pass the name of the variable as a parameter to the function.

Print *all* available variables:

    {{ dump() }}

Print content of `$foo` variable:

    {{ dump(foo) }}

@todo: Add screenshot

### Finding the active template


### Override templates

### Debugging
