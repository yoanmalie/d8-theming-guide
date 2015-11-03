## Theme Hook Suggestions

This hook allows any module or theme to provide alternative theme function or template name suggestions and reorder or remove suggestions provided by `hook_theme_suggestions_HOOK()` or by earlier invocations of this hook.

These theme suggestions will show up in the Twig debug output (when enabled). This allows to create a more complex logic to decide which template file should be used to render the data.

> Don't get confused with the double `hook`. The first hook stands for the name of the **theme or module**, the second stands for the **template**.

**Drupal 7:**

    <?php
    /**
    * Implements hook_preprocess_HOOK() for node templates.
    */
    function MYTHEME_preprocess_node(&$variables) {
      $variables['theme_hook_suggestions'][] = 'node__' . 'first';
      $variables['theme_hook_suggestions'][] = 'node__' . 'second';
    }

**Drupal 8:**

    <?php
    /**
    * Implements hook_theme_suggestions_HOOK_alter() for node templates.
    */
    function MYTHEME_theme_suggestions_node_alter(array &$suggestions, array $variables) {
      $suggestions[] = 'node__' . 'first';
      $suggestions[] = 'node__' . 'second';
    }

To add a template file suggestion for the `page` hook, you would implement `hook_theme_suggestions_page_alter()`.

#### hook_preprocess for suggestions

Each theme hook suggestion will automatically get it's own preprocess function. For the example above, the following two preprocess functions will be available:

    /* for $suggestions[] = 'node__' . 'first'; */
    function hook_preprocess_node__first(&$variables);

    /* for $suggestions[] = 'node__' . 'second'; */
    function hook_preprocess_node__second(&$variables);
