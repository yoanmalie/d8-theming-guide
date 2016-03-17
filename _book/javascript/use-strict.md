## 'use strict'

The `"use strict"` directive is new in JavaScript 1.8.5 and ignored by previous
versions of javascript. The purpose of `"use strict"` is to indicate that the
code should be executed in *strict mode*. This *scrict mode* makes it easier to
write more secure javascript and gives error when using a bad syntax. As an
example you cannot use undeclared variables in *script mode*. This will cause an
error.

> The reason for this is that when you use an undeclared variable, this variable
> becomes a new global variable. This can be dangerous when you accidentally
> mistype the name of a variable.
>
>   var message = 'Hello world';
>
>   …
>
>   msg = 'Bye world';
>
> In the example above, a new variable `message` is new declared. Later in the
> script, this `message` should be changed. Instead, the `msg` variable gets
> changed. Since it's not declared, it will be created as new global variable.
> In *strict mode* hover, the example above will cause an error.
