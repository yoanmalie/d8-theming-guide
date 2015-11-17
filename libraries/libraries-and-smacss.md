## Libraries and SMACSS

When adding css to add library, you are forced to define the SMACSS category the css file belongs to. Drupal takes this category into account when loading in the css files in the `HEAD` of the HTML.

Drupal first first load all the styling from **modules**. It will start by loading all the base styling, although generally modules should not contain any base styling (since this will change the layout for HTML elements on the entire website). Next it will load all of the **layout** styling from modules. Next up will be the **component** styling. The styling for modules will mostly contain this kind of styling, to styling the new UI components this module has introduced.

> As a module developer, it always a good practice to ask for help if you don't have a lot of experience. Kindly ask people for advice, and try to reuse some of the component that are already in core … Dare to take a look at other modules.

**States** styles are, in Drupal core, defined together with the component styling. This is mostly because there just aren't that many states in core components.

Last but definnitly not least, **theme** styling is loaded. Drupal uses the `theme` key, but this category is often reffered to as **skin** (since themes means something else in the Drupal worlds).
