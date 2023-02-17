# PHP Functions

The real power of programming comes from abstraction. Abstraction is the removal or generalization of details to focus attention on things of greater importance.

One of the simplest form of abstraction in computer programming is the creation of functions.

PHP has more than 1000 built-in functions, and in addition you can create your own custom functions.

## PHP Built-in Functions

PHP has overwhelmingly many built-in functions that can be called directly, from within a script, to perform a multitude of tasks.

To find out which function to use for a specific purpose, Google is often your ally, as long as you start each search with the keyword "php".

## PHP User Defined Functions

Besides the built-in PHP functions, it is possible to create your own functions.
Creating functions allows the programmer to hide the details of how the function works and use the name under which it has been created.
In essence, we are teaching the computer how to "do something".

* A function is a block of statements that can be used repeatedly in a program.
* A function will execute only when called.

A user-defined function declaration starts with the word function:
```
function functionName()
{
  code to be executed;
}
```

Note: A function name must start with a letter or an underscore. Function names are NOT case-sensitive.

For clarity of code, give the function a name that reflects what the 
function does.

In the example below, we create a function named "greet()".
The opening curly brace ( { ) indicates the beginning of the function body, and the closing curly brace ( } ) indicates the end of the function body.
The function outputs "Hello world!".
To call the function, just write its name followed by brackets ():
```
<?php
function greet(){
  echo "Hello world!";
}
greet(); // call the function
?>
```

## Function Arguments

Information can be passed to functions through arguments. 
An argument is just like a variable.

Arguments are specified after the function name, inside the parentheses.
You can add as many arguments as you want, just separate them with a comma. 

The following example is of a function with one argument ($name).
When the greet() function is called, we also pass along a name (e.g. Bob), and the name is used inside the function, which outputs a greeting message to anyone whose name is passed as an argument:
```
<?php
function greet($name) {
  echo "Hello $name!<br>";
}
greet("Alice");
greet("Bob");
greet("Carl");
?>
```

The following example has a function with two arguments ($name and $year):
```
<?php
function BoomerGreet($name, $year) {
  
  if(($year >= 1946) && ($year <= 1964))
    echo "Hello $name. You're born in the Baby Boom era!<br>";
  else
    echo "Hello $name.<br>";  
}
BoomerGreet("Alice", 1951);
BoomerGreet("Bob", 1971);
BoomerGreet("Carl", 1991);
?>
```

## PHP is a Loosely Typed Language

We don't have to tell PHP which data type the variable is.

PHP automatically associates a data type to the variable, depending on its value.
Since the data types are not set in a strict sense, you can do things like adding a string to an integer without causing an error.

As of PHP 7, type declarations were added.
This gives us an option to specify the expected data type when declaring a function, and by adding the strict declaration, it will throw a "Fatal Error" if the data type mismatches.

In the following example we try to send both a number and a string to the 
function without using strict:

```
<?php
function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days"); // since strict is NOT enabled "5 days" is changed to int(5), and it will return 10
?>
```

To specify strict we need to set `declare(strict_types=1);`.
This must be on the very first line of the PHP file that contains the type hints.
In the following example we try to send both a number and a string to the function, but here we have added the strict declaration:

```
<?php
declare(strict_types=1); // strict requirement
function addNumbers(int $a, int $b) {
  return $a + $b;
}
echo addNumbers(5, "5 days"); // since strict is enabled and "5 days" is not an integer, an 
error will be thrown
?>
```

The strict declaration forces respect of datatypes like in strictly typed languages.

## Default Argument Value

The following example shows how to use a default parameter. If we call the 
function setHeight() without arguments it takes the default value as argument:
```
<?php
declare(strict_types=1); // strict requirement
function setHeight(int $minheight = 50) {
  echo "The height is : $minheight <br>";
}
setHeight(350);
setHeight(); // will use the default value of 50
?>
```

## Functions return

To let a function return a value, use the return statement:

```
<?php 
declare(strict_types=1); // strict requirement
function sum(int $x, int $y) {
  $z = $x + $y;
  return $z;
}
echo "5 + 10 = " . sum(5, 10) . "<br>";
echo "2 + 4 = " . sum(2, 4);
?>
```

## PHP Return Type Declarations

We can also use a type declaration for the return statement.
With strict_types=1 declared, all type declarations will throw a "Fatal Error" on a type mismatch. This applies to the return type.

To declare a type for the function return, add a colon ( : ) and the type right before the opening curly ( { ) bracket when declaring the function.In the following example we specify the return type for the function:
```
<?php declare(strict_types=1); // strict requirement
function addNumbers(float $a, float $b) : float {
  return $a + $b;
}
echo addNumbers(1.2, 5.2);
?>
```

You can specify a different return type, than the argument types, but make sure the return is the correct type:
```
<?php
declare(strict_types=1); // strict requirement
function addNumbers(float $a, float $b) : int {
  return (int)($a + $b);
}
echo addNumbers(1.2, 5.2); ?>
```

## Passing Arguments by Reference

In PHP, arguments are usually passed by value, which means that a copy of the value is used in the function and the variable that was passed into the function cannot be changed.

When a function argument is passed by reference, changes to the argument also change the variable that was passed in.
To turn a function argument into a reference, the & operator is used:

Use a pass-by-reference argument to update a variable:
```
<?php
function add_five(&$value) {
  $value += 5;
}
$num = 2;
add_five($num);
echo $num;
?>
```