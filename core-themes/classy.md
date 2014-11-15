
## Classy

At DrupalCon Austin (2014) the need for a new core *base* theme came up. This need was part of **Consensus Banana**.

### Consensus Banana

> Where did the **banana** come from?
> 2 years ago at BadCamp, John Albin ([JohnAlbin](https://www.drupal.org/u/johnalbin)) was holding a plastic sword from the pirate fest the day before. It was known as the sword of consensus. At DrupalCon Austin Morten ([mortendk](https://www.drupal.org/u/mortendk)) had a banana that he was using to point to people and ask “so can we agree on X?”. That is how it became the banana of consensus. It was basically a pointing stick.
> - *Scott Reeves*

`<div class="do-not-add-classes-in-drupal-core"></div>`

#### The meta issue

Here's a brief overview of [the meta issue](https://www.drupal.org/node/2289511):

> *Create a new core theme (code name "classy") that contains a copy of the all current core template files; this is for the "sensible 2/3" camp. And then modify all of the core/modules template files to contain minimal classes (only those needed for functionality); this would be for the "clean 1/3" camp. To ensure that Seven and Bartik continue to function properly, they should use "classy" as their base theme.*

#### Technical changes

Technically it comes down to this: The classes from core have been moved into the classy base theme. This was done in two phases. During the first phase the classes have been moved out of preprocess functions and moved into core templates. In the second phase the core template with classes have been moved to Classy and all of the classes have been removed from core template files.

Themers no longer require a base theme like [mothership](https://www.drupal.org/project/mothership) to *keelhaul the div*! A survey showed that no all themers want the same markup. Thanks to Classy, no one has to waist any more time undoing core.

### Classy, a new base theme

Classy is a new `base theme` that *Bartik* and *Seven* will both use.

[Add classy.info.yml to core, set Classy as base theme for Bartik and Seven](https://www.drupal.org/node/2329501)

At DrupalCon Amsterdam, the **classy.info.yml** got commited into Drupal 8 core by Dries. The change record can be found [here](https://www.drupal.org/node/2337467).

***

**Read more**

* Modules Unraveled, episode 119: [The Classy Base Theme for Drupal 8 with Scott Reeves and David Hernandez](https://www.youtube.com/watch?v=uIutb2-Vc50).
* The official change record: [Added a new base theme to core called Classy](https://www.drupal.org/node/2337467)
