## Breakpoints

The *breakpoint* module keeps track of the height, width and resolution breakpoints where a responsive design needs to change in order to respond to different devices being used to view the site. The breakpoint module standardises the use of breakpoints, and enables modules and themes to expose or use each others' breakpoints. The core module does not have a user interface. The breakpoints are stored inside a `{module-or-theme}.breakpoints.yml` file.

The change record can be found here: [Breakpoint added to Drupal 8](https://www.drupal.org/node/1813914)

### Breakpoints configuration

Both themes and modules can define breakpoints by creating a configuration file called `{name}.breakpoints.yml` where `{name}` is the name of your theme or module.

To get a good example, let's take a look at `bartik.breakpoints.yml`:

    bartik.mobile:
      label: mobile
      mediaQuery: '(min-width: 0px)'
      weight: 0
      multipliers:
        - 1x
    bartik.narrow:
      label: narrow
      mediaQuery: 'all and (min-width: 560px) and (max-width: 850px)'
      weight: 1
      multipliers:
        - 1x
    bartik.wide:
      label: wide
      mediaQuery: 'all and (min-width: 851px)'
      weight: 2
      multipliers:
        - 1x

Each breakpoint has it's own identifier. Bartik has 3 unique breakpoints: *mobile*, *narrow* and *wide*. Each breakpoint is defined as `{module or theme name}.{label}`, with `bartik.mobile` as an example. The name of the module or theme is used to make sure the identifier is unique. This way, modules can include breakpoints from each other.

### label

Human readable label for breakpoint. It should be unique within a module or theme.

### mediaQuery

The media query for the breakpoint.

### weight

Weight used for ordering breakpoints.

### multipliers

Breakpoint multipliers. Multipliers are a measure of the viewport's device resolution, defined as the ratio between the physical pixel size of the active device and the device-independent pixel size. The breakpoint module defines multipliers of 1, 1.5 and 2. When defining breakpoints, modules and themes can define which multipliers apply to each breakpoint.
