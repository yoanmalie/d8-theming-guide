# Template files (Twig)

Twig is a PHP-based compiled templating language. When your web page renders, the Twig engine takes the template and converts it into a 'compiled' PHP template which it stores in a protected directory in sites/default/files/php_storage/... The compilation is done once. Template files are cached for reuse and are recompiled on clearing the Twig cache.
