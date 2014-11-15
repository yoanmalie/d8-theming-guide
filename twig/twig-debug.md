## Twig debug

An **awesome** new feature from the Twig engine is the debug tool. It allows you to trace where the template comes from. To enable Twig Debugging, all you have to do is set the `debug` variable in the `twig.config ` to `true`.

    `sites/default/services.yml`:
    ---

    parameters:
      twig.config:
        debug: true # originally false

[@todo:]
- How to find the active template
- Overriding template
- Debug array.
- Add screenshot
