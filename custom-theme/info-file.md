## Creating an info file

### A simple .info.yml file

Again, if you're familiar with Drupal 7 theming, your first idea might be to start with creating an `.info` file. In Drupal 8, `.info` files are replaced by `.info.yml` files ([read the change record](https://www.drupal.org/node/1935708)). These files are parsed using the Symphony YAML Component. This change also applies for modules and installation profiles. They both require a `.info.yml` now, instead of the old `.info` file. Once you've created the file, it's time to add the write the first line of code.

	name: Awesome Theme

Fairly simple. This is the name of the theme. It's the name that also appears on the *Appearance* page, where you can activate your theme.

	description: 'An awesome D8 theme.'

A theme description. This description is also displayed on the *Appearance* page.

	package: Custom

The package in which your theme lives. For the core themes, this package is of course `core`.

	type: theme

Since the `info.yml` files are used for besides themes also used for modules and profiles, this line lets Drupal know if it's a theme, module or a profile.

	version: 1.0

The version of the theme.

	core: 8.x

The version of Drupal core the theme requires.

#### Using a base theme

	base theme: classy

The line above gives you the power to extend from a base theme. This line can be found in both `bartik.info.yml` and  `seven.info.yml`, since these two core themes extend **Classy**.

#### *.info.yml

To wrap things up, this is our `.info.yml` file so far:

	name: Awesome Theme
	description: 'An awesome D8 theme.'
	base theme: classy
	package: Custom
	type: theme
	version: 1.0
	core: 8.x

Save this as `{theme_name}.info.yml` (`awesome.info.yml`) inside the created custom theme directory (eg. `themes/custom/example/example.info.yml`). Now navigate to `admin/appearance` and see your theme displayed. You can now even enable the theme. Hooray!

#### Adding a screenshot

When navigation to the appearance page, you might notice a *no screenshot* image for our theme. This is because no screenshot has been found (duh!). A screenshot is automatically detected and displayed if the filename is `screenshot.png`. If we add this file, we would see the screenshot on the appearance page.

Otherwise you can manually add a screenshot with the following line:

	screenshot: otherfilename.png

If everything went well, you should be able to see the screenshot:

![https://raw.githubusercontent.com/sqndr/d8-theming-guide/master/img/awesome_theme_screenshot.png](https://raw.githubusercontent.com/sqndr/d8-theming-guide/master/img/awesome_theme_screenshot.png)

The screenshot of cause doesn't have to be a `*.png`. It can be an `*.svg` or even an animated `*.gif`

**Conclusion:** the filename for a screenshot does not have to be `screenshot.png`, as long as it is defined in the *{theme}.info.yml* file.

#### Adding stylesheets

In Drupal 8, both stylesheets and scripts should be added using libraries. Read more on how to create a library with css and javascript files in the **libraries** chapter.

#### Removing stylesheets

Alternatively, a stylesheet can also be removed.

	# Remove a CSS file:​
	stylesheets-remove:
	  - core/assets/vendor/jquery.ui/themes/base/dialog.css

To remove a stylesheet, the full path to the css file should be used (instead of just a file name). This due to the fact that multiple css files can have the same name.

In cases where a Drupal core asset is being removed the full file path is needed. In cases where the file is part of a library that belongs to a module or theme, a token can be used.

> When using a token, it needs to be quoted because `@` is a reserved indicator in YAML.

	# Removing a stylesheet from Bartik using the @ token.
	stylesheets-remove:
  	- '@bartik/css/style.css'

#### Regions

Regions can be defined using the `regions` tag. Here is an example where 3 regions are defined: a *header*, a *content* and a *footer* region:

	# Regions
	regions:
	  header: 'Header'
	  content: 'Content'
	  footer: 'Footer'

#### Regions hidden

The `regions_hidden` can be applied to any previous defined *regions*. Regions with this attribute will not show up on the block administration page. This means they can't have blocks assigned to them by ordinary mechanisms. Drupal uses this feature to protect the special 'page_top' and 'page_bottom' regions from adventurous themers. This can be used by module writers and theme writers to protect a given region from having unexpected content inserted into the output. The `seven.info.yml` contains this tag, in order to *hide* the 'Sidebar First' region.

	regions_hidden:
  	- sidebar_first
