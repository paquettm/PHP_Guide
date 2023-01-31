# PHP Data Types

Variables can store data of different types, and different data types can do 
different things.

PHP supports the following data types:
* String
* Integer
* Float (floating point numbers - PHP use doubles)
* Boolean
* Array
* Object
* Enumerations
* NULL
* Resource

## Strings

A string is a sequence of characters, like "Hello world!".

A string can be any text inside quotes. You can use single or double quotes:
```
<?php
$x = "Hello world!";
$y = 'Hello world!';
echo $x;
echo "<br>";
echo $y;
?>
```
Note: There are important differences between single and double quotes.
* Strings enclosed between single quotations are not interpreted: what you see is what you get, but you must escape ' and \ to include them in strings:`$text = 'I\'ve been meaning to use more backslashes (\\) in my strings'; `
* Strings enclised between double quotations are interpreted for many character sequences to include variable values, tabs, line feeds, etc., e.g., `$text = " I like \t tabs and \n changing lines once in a while.";`

## Integer

An integer is a number between -2,147,483,648 and 2,147,483,647 that has no fractional part, i.e., the number has no digits after a decimal point.

Rules for integers:
* An integer must have at least one digit (digits = the symbols 0-9 for decimal numbers)
* An integer do not have a decimal point
* An integer can be either positive or negative
* Integers can be specified in: decimal (base 10), hexadecimal (base 16), octal (base 
  8), or binary (base 2) notation

  In the following example $a is an integer. The variable $a is set different integer values expressed in decimal, octal, hexadecimal, and binary formats. The PHP var_dump() function returns the data type and value:
```
<?php
$a = 1234; // decimal number
$a = 0123; // octal number (equivalent to 83 decimal)
$a = 0o123; // octal number (as of PHP 8.1.0)
$a = 0x1A; // hexadecimal number (equivalent to 26 decimal)
$a = 0b11111111; // binary number (equivalent to 255 decimal)
$a = 1_234_567; // decimal number (as of PHP 7.4.0)
var_dump($a);
?>
```

## Float

A float (floating point number) is a number with a decimal point or a number in exponential form.

In the following example, all variables are assigned float-type values. The PHP var_dump() 
function returns the data type and value of each variable:
```
<?php
$a = 1.234; 
$b = 1.2e3; 
$c = 7E-10;
$d = 1_234.567; // as of PHP 7.4.0
var_dump($a);
var_dump($b);
var_dump($c);
var_dump($d);
?>
```

## Boolean

A Boolean can store two possible truth values: true or false.

```
 $x = true;
 $y = false;
```
Boolean expressions evaluate to a Boolean value and are most often used in control structures to select how to continue the program execution.

## Array

An array can store multiple values in one single variable.

In the following example $cars is an array. An array can be denoted by the array() function or by delimiting elements with square brackets "[]":
```
<?php 
$cars = array('Jeep','Toyota','Subaru');
$cars = ['Jeep','Toyota','Subaru'];
var_dump($cars);
?>
```

In PHP, arrays are ordered maps, an object type that associates keys with values. In th above example, keys are implicitly integers from 0 to 2. Below, we set string values as keys to values using the 'key'=>'value' notation.

```
<?php 
$inventory = ['Apples'=>3,'Oranges'=>21,'Peaches'=>0];
var_dump($inventory);
?>
```

## Object

Classes and objects are the two main aspects of object-oriented programming.

A class is a template for objects, and an object is an instance of a class. We can also say that a class is a definition of an object type.

When objects are created from a class definition, they are built with the properties and 
behaviours (methods) from the class, but each object can have different values for the 
properties.

For example, let's imagine a class Person with a $name property as well as a greting behaviour. We can create two instances of the class Person with the names 'Alice' and 'Bob'.

If you create a \_\_construct() function, PHP will automatically call this 
function when you create an object from that class with the `new` keyword.
```
<?php
class Person {
  public $name;
  public function __construct($name) {
    $this->name = $name;
  }

  public function greeting() {
    return "Hi! My name is " . $this->name . "!";
  }
}

$person = new Person("Alice");
echo $person->greeting();
echo "<br>";
$person = new Person("Bob");
echo $person->greeting();
?>
```

## NULL Value

Null is a special data type which can have only one value: NULL.

A variable of data type NULL is a variable that has no value assigned to it.

When a variable is created without a value, it is automatically assigned a value of NULL.
Variables can also be emptied by setting the value to NULL:
```
<?php
$x = "Hello world!";
$x = null;
var_dump($x);
?>
```

## Enumerations

Enumerations provide a way for programmers to define a closed set of possible values for a type. For example, below, we define the suit type to hold 4 possible constants:
```
<?php
enum Suit
{
    case Hearts;
    case Diamonds;
    case Clubs;
    case Spades;
}

function do_stuff(Suit $s)
{
    // ...
}

do_stuff(Suit::Spades);
?>
```

## Resource

A resource is not like other data types. It is a reference to an operating-system resource such as
* a file pointer
* a connection to another application, such as a relational database management system

We will discuss how to connect to databases and open files in later chapters.

A full list of functions that return resources can be found at [https://www.php.net/manual/en/resource.php](https://www.php.net/manual/en/resource.php).

