## Twig debug

An **awesome** new feature from the Twig engine is the debug tool. It allows you to trace where the template comes from. To enable Twig Debugging, all you have to do is set the `debug` variable in the `twig.config ` to `true`.

    `sites/default/services.yml`:
    ---

    parameters:
      twig.config:
        debug: true # originally false

### Finding a variable.

To print all the available variables (in a template file), `dump()` can be used. To print the content of a specific variable, pass the name of the variable as a parameter to the function.

Print *all* available variables:

    {{ dump() }}

Print content of `foo` variable:

    {{ dump(foo) }}
    
[@todo:] Add screenshot of dump().



[@todo:]
- How to find the active template
- Overriding template
- Debug array.
- Add screenshot
