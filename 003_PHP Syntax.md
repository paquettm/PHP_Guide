# PHP Syntax

In the context of Web aplications, PHP scripts execute on the server, and the resulting output is sent back to the requesting browser.

## Basic PHP Syntax

A PHP script block starts with <?php and ends with ?>, as follows:
```
<?php
// PHP code goes here
?>
```

PHP files can contain 0 or more PHP script blocks. 

The default file extension for PHP files is ".php".

A PHP file can contain other content and often will be seen with HTML tags, and some PHP scripting code. Anything outside of PHP script blocks gets output as-is.

Below, we have an example of a simple PHP file, with a PHP script that uses a built-in PHP function "echo" to output the text "Hello World!" on a web page:

```
<!DOCTYPE html>
<html>
   <body>
   <h1>My first PHP page</h1>
   <?php
      echo "Hello World!";
   ?>
   </body>
</html>
```
Note: PHP statements end with a semicolon (;), just like Java code.

When the PHP script block contains only a single echo instruction, we can use PHP short echo tags <?= expression ?> to replace <?php echo expression; ?> as follows:

```
<!DOCTYPE html>
<html>
   <body>
      <h1>My first PHP page</h1>
      <?= "Hello World!" ?>
   </body>
</html>
```

## PHP Case Sensitivity

In PHP, keywords (e.g. if, else, while, echo, etc.), classes, functions, and user-defined functions are not case-sensitive.

In the example below, all three echo statements below are equal and legal:

```
<!DOCTYPE html>
<html>
   <body>
   <?php
      ECHO "Hello World!<br>";
      echo "Hello World!<br>";
      EcHo "Hello World!<br>";
   ?>
   </body>
</html>
```
In other words, PHP may sometimes be forgiving. 

However, variable names are case-sensitive.

In the example below, only the first statement will display the value of the $color variable because $color, $COLOR, and $coLOR are treated as three different variables:

```
<!DOCTYPE html>
<html>
   <body>
   <?php
      $color = "red";
      echo "My car is " . $color . "<br>";
      echo "My house is " . $COLOR . "<br>";
      echo "My boat is " . $coLOR . "<br>";
   ?>
   </body>
</html>
```

## Comments in PHP

A comment in PHP code is a line that is not executed as a part of the 
program. Its only purpose is to be read by someone who is looking at the code.

Comments can be used to:
* Let others understand your code
* Remind yourself of what you did - Most programmers have experienced coming back to their own work a year or two later and having to re-figure out what they did. Comments can remind you of what you were thinking when you wrote the codePHP supports several ways of commenting.

Syntax for single-line comments:

```
<!DOCTYPE html>
<html>
   <body>
      <?php
      // This is a single-line comment
      # This is also a single-line comment
      ?>
   </body>
</html>
```

Syntax for multiple-line comments:

```
<!DOCTYPE html>
<html>
   <body>
      <?php
      /*
      This is a multiple-line comment block
      that spans over multiplelines
      */
      ?>
   </body>
</html>
```

Using comments to leave out parts of the code:

```
<!DOCTYPE html>
<html>
   <body>
   <?php
     // You can also use comments to leave out parts of a code line
     $x = 5 /* + 15 */ + 5;
     echo $x;
   ?>
   </body>
</html>
```

## Standardization and Style Guide

The [PHP Framework Interoperability Group (php-fig)](https://www.php-fig.org/) is "a group of established PHP projects whose goal is to talk about commonalities between \[their\] projects and find ways \[to\] work better together."

PHP-fig makes PHP Standard Recommendations (PSRs) that professional PHP programmers follow to ensure that their code remains usable and compatible with mainstream PHP frameworks and can be used as modules if registered with tools for dependency management such as [Composer](https://getcomposer.org/).

As part of these recommendations, PSR-1: Basic Coding Standard is the basic style guide to follow for all PHP coding. It contains all recommendations about proper identifier casing (when/where to use upper/lower case), among others. The standard can be found at [https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md), and [https://www.php-fig.org/psr/psr-1/](https://www.php-fig.org/psr/psr-1/).