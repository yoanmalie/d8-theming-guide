### Multilingual in Javascript

The Drupal core javascript library (`core/drupal`) ships with two functions to support multilingual in Javascript. `Drupal.t()` and `Drupal.formatPlural()` are two functions available, that work just like their PHP equivalents:

**Drupal.t()**

> **PHP**: ?

    var close = Drupal.t('Close');
    var nodesOfType = Drupal.t('Showing nodes of @type', {@type: nodeType});

**Drupal.formatPlural()**

> **PHP**: \Drupal\Core\StringTranslation\TranslationInterface::formatPlural()

    var nodesCount = Drupal.formatPlural(count, '1 node', '@count nodes');
    var nodesCountOfType = Drupal.formatPlural(count, '1 node of @type', '@count nodes of @type', {@type: nodeType});
