# Numbers

One thing to notice about PHP is that it provides automatic data type 
conversion.

If you assign an integer value to a variable, the type of that variable will be integer. 
Then, if you assign a string to the same variable, the type will change to string.

This automatic conversion can sometimes break your code.

## Integers

2, 256, -256, 10358, -179567 are examples of integers.

An integer is a number without any decimal part.

An integer type value is a number, without digits after the decimal point, between -2147483648 and 2147483647 in 32 bit systems, and between -9223372036854775808 and 9223372036854775807 in 64 bit systems.
Any value outside these specified intervals, will be stored as float.
Any value inside these intervals but specified with a decimal point, even if the digits are zero (0), will be stored as a float.

Note that even if the result of an expression is a whole number, if the expression contains a floating-point number, the result is a float, e.g.,  4 * 2.5 is 10.0, a float, because the float 2.5 is part of the expression.

Here are some rules for integers:
* An integer must have at least one digit (0 counts as a digit)
* An integer must NOT have a decimal point
* An integer can be either positive or negative
* Integers can be specified in three formats: decimal (10-based), hexadecimal (16-based - prefixed with 0x) or octal (8-based - prefixed with 0 or 0o)

PHP has the following predefined constants for integers:
* PHP_INT_MAX - The largest integer supported
* PHP_INT_MIN - The smallest integer supported
* PHP_INT_SIZE - The size of an integer in bytes

PHP has the following functions to check if the type of a variable is 
integer:
* is_int()
* is_integer() - alias of is_int()
* is_long() - alias of is_int()

Check if the type of a variable is integer:

```
<?php
$x = 5985;
var_dump(is_int($x));
$x = 59.85;
var_dump(is_int($x));
?>
 ```

## Floats

A float is a number with a decimal point or a number in exponential form.

2.0, 256.4, 10.358, 7.64E+5, 5.56E-5 are all examples of floats.

The float data type can commonly store a value up to 1.7976931348623E+308 
(platform dependent), and have a maximum precision of 14 digits.

PHP has the following predefined constants for floats (from PHP 7.2):
* PHP_FLOAT_MAX - The largest representable floating point number
* PHP_FLOAT_MIN - The smallest representable positive floating point number
* - PHP_FLOAT_MAX - The smallest representable negative floating point 
  number
* PHP_FLOAT_DIG - The number of decimal digits that can be rounded into a 
  float and back without precision loss
* PHP_FLOAT_EPSILON - The smallest representable positive number x, so that 
  x + 1.0 != 1.0, i.e., the smallest number that, when added to 1.0, will be significant enough to make the sum larger than 1.0

For the last bullet above, it is important to remember that floting point variables have a precision limited by the size of their mantissa, in turn limited by their size in number of bytes.

PHP has the following functions to check if the type of a variable is 
float:
* is_float()
* is_double() - alias of is_float()

Check if the type of a variable is float:
```
<?php 
$x = 10.365;
var_dump(is_float($x))
;?>
```

## Infinity

In PHP, a numerical value that is larger than PHP_FLOAT_MAX is considered *infinite*.

PHP has the following functions to check if a numerical value is *finite* or 
*infinite*:
* [is_finite()](func_math_is_finite.asp)
* [is_infinite()](func_math_is_infinite.asp)

However, the PHP var_dump() function returns the data type and value.
Check if a numerical value is finite or infinite:
```
<?php 
$x = 1.9e411;
var_dump($x);
?> 
```

## NaN

NaN stands for Not a Number.

NaN is used for impossible mathematical operations.

PHP has the following functions to check if a value is not a number:
* [is_nan()](func_math_is_nan.asp)

However, the PHP var_dump() function returns the data type and value.
Invalid calculation will return a NaN value:
```
<?php
$x = acos(8);
var_dump($x);
?> 
```

## Numerical Strings

The PHP is_numeric() function can be used to find whether a variable is 
numeric. The function returns true if the variable is a number or a numeric 
string, false otherwise.Check if the variable is numeric:

```
<?php 
$x = 5985;
var_dump(is_numeric($x));
$x = "5985";
var_dump(is_numeric($x));
$x = "59.85" + 100;
var_dump(is_numeric($x));
$x = "Hello";
var_dump(is_numeric($x));
?>
```

Note: From PHP 7.0: The is_numeric() function will return 
FALSE for numeric strings in hexadecimal form (e.g. 0xf4c3b00c), as they are no 
longer considered as numeric strings.

## Casting Strings and Floats to Integers

Sometimes you need to cast a numerical value into another data type.

The (int), (integer), or intval() function are often used to convert a value 
to an integer.
Cast float and string to integer:

```
<?php
// Cast float to int 
$x = 23465.768;
$int_cast = (int)$x;
echo $int_cast;
echo "<br>";
// Cast string to int
$x = "23465.768";
$int_cast = (int)$x;
echo $int_cast;
?>
```
