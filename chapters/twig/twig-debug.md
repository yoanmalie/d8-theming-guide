## Twig debug

An **awesome** new feature from the Twig engine is the debug tool. It allows you to trace where the template comes from. To enable Twig Debugging, all you have to do is set the `debug` variable in the `twig.config ` to `true`. Navigate to `sites/default/services.yml` to change the it:

  parameters:
    twig.config:
    debug: false

[@todo:]
- How to find the active template
- Overriding template
- Debug array.
- Add screenshot
