# Mathematical functions and operators

PHP has a set of math functions that allows you to perform mathematical tasks on numbers.

## pi()

The pi() function returns the value of PI:

```
<?php
echo(pi()); // outputs 3.1415926535898
?>
```

## min() and max()

The min() and max() functions can be used to find the lowest or highest value in a list of arguments:
```
<?php
echo(min(0, 150, 30, 20, -8, -200)); // outputs -200
echo(max(0, 150, 30, 20, -8, -200)); // outputs 150
?>
```

## abs()

The abs() function returns the absolute (positive) value of a number:

```
<?php
echo(abs(-6.7)); // outputs 6.7
?>
```

## sqrt()

The sqrt() function returns the square root of a number:

```
<?php
echo(sqrt(64)); // outputs 8
?>
```

## round()

The round() function rounds a floating-point number to its nearest integer if no precision is specified and if a positive integer is provided as the second parameter, then it will round to that decimal position (precision):

```
<?php
echo(round(0.60)); // outputs 1
echo(round(0.49)); // outputs 0
echo(round(0.49,1)); // outputs 0.5
echo(round(0.44,1)); // outputs 0.4
?>
```

## Random Numbers

The rand() function generates a random number:

```
<?php
echo(rand());
?>
```

To get more control over the random number, you can add the optional min and max parameters to specify the lowest integer and the highest integer to be returned.For example, if you want a random integer between 10 and 100 (inclusive), use 
rand(10, 100):

```
<?php
echo(rand(10, 100));
?>
```

## Complete PHP Math Reference

For a complete reference of all math functions, go to the [PHP Math Reference](https://www.php.net/manual/en/ref.math.php)