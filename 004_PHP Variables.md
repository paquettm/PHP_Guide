# PHP Variables

Variables are "containers" to store information.

## Creating (Declaring) PHP Variables

In PHP, a variable starts with the $ sign, followed by the name of the variable:

```
<?php
$txt = "Hello world!";
$x = 5;
$y = 10.5;
?>
```

After the execution of the statements above, the variable `$txt` will hold the value `Hello world!`, the variable `$x` will hold the value `5`, and the variable `$y` will hold the value 
`10.5`.

Notice the use of quotation marks when assigning a text value to a variable.

Notice in the above example that PHP variables can be initialized without declaring them first, i.e., we can set values to them without first stating that the variable exist. This is true when in an instruction block.
We will see later cases when variables need to be declared, e.g., when declaring class properties.

Think of variables as containers for storing data.

## PHP Variables

A variable can have a short name (like x and y) or a more descriptive name (age, carName, totalVolume).

Rules for PHP variables:
* Variable names are always preceded with $ to tell the PHP interpreter that what follows is a variable name. This is helpful to differentiate variables from functions, classes, constants, etc.
* A variable name must start with a letter or the underscore (\_) character
* A variable name cannot start with a number
* A variable name can only contain alpha-numeric characters and underscores (A-Z, a-z, 0-9, and \_)
* **Variable names are case-sensitive ($age and $AGE are two different variables)**

## Outputting Variable Data

The PHP echo statement is often used to output data to the screen.

The following example will show how to output text and a variable:
```
<?php
$txt = "Jane";
echo "Tarzan love $txt!";?>
```
Notice that above, we place a variable between double quotation marks, in line with other text. The string will be read and the variable will be replaced by its value within that string.

The following example uses the `.` concatenation operator to concatenate (glue) strings together. The code will produce the same output as the previous example.
```
<?php
$txt = "Jane";
 echo "Tarzan love " . $txt . "!";
?>
```
The following example will first output a formula for the sum of two numbers, `5 + 4 = `, followed by the sum of the two variables, `9`:
```
<?php
 $x = 5;
 $y = 4;
 echo "$x + $y = ";
 echo $x + $y;
?>
```

Note: We will learn more details about the echo statement in the coming chapters.

## PHP is a Loosely Typed Language

In strongly typed languages, such as C, C++, C#, Java, and Python, variable are declared to contain a specific type of data, and other data types can't be placed within these variables before first converting to data to the appropriate data type.

In loosely typed languaged, it may be possible to replace data from one type to another within a variable without causing an exception or a warning.

In the example above, notice that we did not have to tell PHP which data type the variable is.

PHP automatically associates a data type to the variable, depending on its value. 

In PHP 7, type declarations were added. This gives an option to specify the data type expected when declaring a function. By enabling the strict type in each file where it is desred with the `declare(strict_types=1);` instruction, type errors will throw a "Fatal Error".

You will learn more about strict and non-strict requirements, and data type declarations in the PHP Functions chapter.[PHP Functions](024_php_functions.md)

## Variable Scope
Note that accessibility of variables is subject to [scope](025_Variable_Scope.md), the places where you can see and access them in the code. Before studying scope, we must discuss a few contexts where code can be found.