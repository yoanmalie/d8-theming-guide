# Libraries

## The history of libraries, part 1

During the early development of Drupal 8, assets such as javascript and stylesheets had their own, different way of getting imported into themes. Importing a custom javascript file was done using the `scripts` property inside the `.info.yml`-file of the theme. To import stylesheets, the `stylesheets` property was used. This was more or tell how it was done in Drupal 7. Here is an example from a Drupal 7 `theme.info` file.

    ...

    # Adding stylesheets
    stylesheets[all][] = css/styles.css
    stylesheets[print][] = css/print.css

    # Adding javascript files
    styles[] = js/script.js


    ...

An alternative path was chosen. Javascript maintainer **_nod** created an issue on [using AMD for JS architecture](https://www.drupal.org/node/1542344). The patch for the issue however became so big, a separate issue was created that handled the splitting up of the dependencies. The patch from this issue - [Explicitly declare all JS dependencies, don't use drupal_add_js](https://www.drupal.org/node/1737148) - where all javascript files are declared as libraries and added the relevant dependencies to the scripts, got committed about two weeks after the creation. The original issue [**AMD architecture**] however was posponed to a later Drupal release (Drupal 9.x).

## {}.libraries.yml

Libraries are declared inside a `*.libraries.yml` file (in the early stages of Drupal 8, this was done using `hook_library_info`. Since this was one of the last remaining hooks in Drupal 8, it got [replaced by a `*.libraries.yml` file](https://www.drupal.org/node/2201089)). The file should be in the root directory of the theme (or module).

    # example.libraries.yml

    base:
      version: 1.x
      js:
        js/scripts.js: {}
      css:
        component:
          css/components/component.css: {}
      dependencies:
        - core/drupal
        - core/jquery

Inside the `.info.yml` file the library can be included into our theme, using the `libraries` property.

    # example.info.yml

    libraries:
      - example/base

This means the *example* theme has a dependency on the `base` library (from the *example* theme/module); `example/base`. The `base` library itself contains a single javascript file (`scripts.js`), a css file (categoried as a component) and has dependencies on the `drupal` and `jquery` library from core.

## The history of libraries, part 2

Coming from this change, the `scripts` tag from the `.info.yml`, had to be removed and replaced with the `libraries` property. This ment scripts were include using the `libraries` property and a `libraries.yml` file. Stylesheets however (in themes) were still included using the `stylesheets` property:

**_nod**:

> remove scripts[] from info files and replace it with library[] …

> stylesheets[] can be kept as is, it's totally fair to add a single css file without dependencies. It's highly unlikely for scripts, they will need to depend on jquery, drupal.js 99% of the time.

It became clear this new way of adding assets had some major advantages. Wim Leers created a new issue stating [Themes should use libraries, not individual stylesheets](https://www.drupal.org/node/2377397). This is where the `stylesheets` property from the `.info` file got removed to have a unified way for adding assets libraries.

## The advantages of libraries and dependencies

Copied from the issue summary of [2377397](https://www.drupal.org/node/2377397):

1. dependencies, hence a step towards getting rid of weights
2. one uniformly applied system for modules and themes alike
3. themes are also forced to think about categorisation in their CSS
4. libraries can contain CSS and JS as logically associated units, and can declare dependencies on other libraries
5. themes are encouraged to create a library per component/topic/logical unit and hence are encouraged to not load all their CSS on all pages anymore, but to attach it when appropriate in a preprocess hook and/or only on the relevant pages via hook_page_attachments_alter()

## Summary



## Core libraries

Drupal 8 doesn't load any additional scripts by default. This also means that a library like [jQuery is not included](https://www.drupal.org/node/1541860) on every page any more. This is mostly due to performance reasons. You have to declare jQuery (or any other core library) as a dependency in order to use it.

A quick overview of the of some of the core libraries.

> To get a **complete overview** of all the core libraries, take a look inside `core/core.libraries.yml`.

- `core/drupal`

We need `core/drupal` in order to take advantage of the `Drupal.behaviors`.

- `core/jquery`

To include the Drupal core version of jQuery, we add `core/jquery`.

- `core/jquery.once`

A jQuery plugin allowing to only apply a function once to an element.
