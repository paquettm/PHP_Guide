# PHP Variable Scope and Lifetime

In PHP, variables can be declared anywhere in the script.

The scope of a variable is the part of the script where the variable can be referenced/used.

PHP has three different variable scopes:
* local
* global
* static

## Global and Local Scope

A variable declared outside all functions has a **global** scope and can not directly be accessed within a function body, which has local scope, e.g.,
```
<?php
$x = 5; // global scope
function myTest() {
  // using x inside this function will generate an error
  echo "<p>Variable x inside function is: $x</p>";
} 
myTest();
echo "<p>Variable x outside function is: $x</p>";
?>
```
Above, since no local variable `$x` is declared, and because the global variable $x is not accessible from the local scope, the echo statement will generate a warning or error (depending on the [error_reporting level](https://www.php.net/manual/en/function.error-reporting.php).


A variable declared within a function has a **local** scope and can only 
be accessed within that function, e.g., 
```
<?php
function myTest() {
  $x = 5; 
  // local scope
  echo "<p>Variable x inside function is: $x</p>";
} 
myTest();
// using x outside the function will generate an error
echo "<p>Variable x outside function is: $x</p>";
?>
```
You can have local variables with the same name in different functions, 
because local variables are only recognized within the function where they are 
declared.

## PHP The global Keyword
It is possible to refernce a variable with global scope within the local scope of a function, as long as we declare a local reference to this variable. This is done with the `global` keyword, e.g., 
```
<?php
$x = 5;
$y = 10;
function myTest()
{
  global $x, $y;
  $y = $x + $y;
}
myTest();
echo $y; // outputs 15
?>
```
Not that the above example works in the expected way only if $x and $y were declared in the global scope, i.e., outside any local scope.

PHP also stores all global variables in an array called $GLOBALS. In arrays, data gets stored at a locatin that is indicated by its *index*. Array data can be accessed by providing their index between square brackets `[]` as follows: 
`$GLOBALS[index]` 

For the `\$GLOBALS` array, the index of each element is the name of that variable, without the `\$`, and expressed as a string, e.g., `\$GLOBALS['x']` accesses the global variable `\$x`.

The example above can be rewritten as follows:
```
<?php
$x = 5;
$y = 10;

function myTest()
{
  $GLOBALS['y'] = $GLOBALS['x'] + $GLOBALS['y'];
} 

myTest();
echo $y; // outputs 15
?>
```

## Variable Lifetime

All variables have a lifetime limited to the lifetime of their scope.

In other words, **with the exception of static variables** explained below:
* If a variable is a local variable declared within a function body, it will exist from the time it has been declared until the time that this function returns.
* If a variable is an object property, it will exist from the time that the object is declared and its property is declared until the time when the property is unset or the object is deleted by [garbage collection](https://www.php.net/manual/en/features.gc.php) or any other explicit unsetting.
* If a variable is global, it will exist from the time that it is declared until the time the program exits or when it is unset explicitly.

## PHP The static Keyword

When a function returns from its execution, its local variables are deleted. However, sometimes we want a local variable NOT to be deleted. We need it for a further job.

To do this, we declare a static variable within this function. Static variables are not tied to a function execution or a class instance but rather to its function or class definition. As such, it is declared once only (the first time its declaration code runs) and remains in memory throughout the entire program execution. Its value can be modified and accessed persistently across multiple function executions or class instances, i.e., the value retains changed between each access/modification.
```
<?php
function myTest()
{
  static $x = 0;
  echo $x;
  $x++;
}
myTest();
myTest();
myTest();
?>
```

Then, each time the function is called, that variable will still have the 
information it contained from the last time the function was called.

Note: The variable is still local to the function.

