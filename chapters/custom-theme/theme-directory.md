## The /themes directory

All right. Now is the time to get really excited. We're about to create a Drupal 8 theme! The question that raises is: where should this theme be located, where should I put the files?

> If you're familiar with Drupal 7 theming, the first place for you to look at would be `drupal/sites/all/themes/{custom/}` (the place where all your custom themes lived in Drupal 7).

In Drupal 8, this location has changed. Custom and contrib themes now live in `drupal/themes`. Also notice that (custom and contrib) modules now live inside `drupal/modules` (instead of drupal/sites/all/modules/).

> Did you notice {*custom*}? It's always a good practice to separate the contrib themes (the one's you've been downloading from d.o) and the ones you've written yourself. This can simply be done by creating two folders inside the `themes` directory:

> `contrib`: for contrib themes  
> `custom`: for custom themes

### Create your custom theme directory

Let's create an `example` directory inside `themes/custom`, resulting in `themes/custom/example`. Inside this directory, all the code for our custom theme will live.
