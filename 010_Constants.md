# Constants

A constant is an identifier (name) for a simple value.

Contrary to variables, once constants are defined, they cannot be changed or undefined.

A valid constant name starts with a letter or underscore. Contrary to variables, no $ sign should precede the name when declaring or accessing the constant.

Unlike variables, constants are accessible throughout all scopes of the entire script once their declaration has run.

## Create a PHP Constant

To create a constant, use the define() function.
```
 define(name, value, case-insensitive = false)
 ```
 Parameters:
* name: Specifies the name of the constant
* value: Specifies the value of the constant
* case-insensitive: Specifies whether the constant name should be case-insensitive. Default is false

Note: Prior to PHP 8.0.0, constants defined using the define() function may be case-insensitive.

Create a constant with a case-sensitive name:
```
<?php
define("GREETING", "Welcome!");
echo GREETING;
?>
```

Create a constant with a case-insensitive name:
```
<?php
define("GREETING", "Welcome!", true);
echo greeting;
?>
```

## Constant Arrays

As of PHP 7.0, you can create an Array constant using the define() function, for example,

```
<?php
define("cars", ["Jeep","Toyota","Lexus"]);
echo cars[0];
?>
```

## Constants are Global

Constants are automatically global and can be used across the entire script once it has been defined.
Here, the word global is used in the sense that the constant is accessible in all scopes, for example,

```
<?php
define("GREETING", "Welcome!");
function myTest() {
    echo GREETING;
}
myTest();
?>
```
