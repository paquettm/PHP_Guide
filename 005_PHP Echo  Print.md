# PHP echo and print Statements

With PHP, there are two basic ways to get output: echo and print.

## PHP echo and print Statements

echo and print are both used to output data to the default output.
The differences are small:
* echo has no return value while print has a return value of 1 so it can be used in expressions.
* echo can take multiple parameters (although such usage is rare) 
while print can take one argument.
* echo is marginally faster than print.

## The PHP echo Statement

The echo statement can be used with or without parentheses: 
echo or echo().

The following example shows how to output text with the echo 
command (notice that the text can contain HTML markup):

```
<?php
 echo "<h2>Tarzan love Jane!</h2>";
 echo "Why did Tarzan quit the jungle?<br>";
 echo "Because he wanted to branch out<br>";
 echo "and ", "explore ", "new ", "trees!";
?>
```

The following example shows how to output text and variables with the echo 
statement:

```
<?php
$txt1 = "Why did Tarzan, Jane, and Cheeta go to the zoo?";
$txt2 = "To see the other primates.";
$x = 5;
$y = 4;
echo "<p>Q: " . $txt1 . "<br />";
echo "A: " . $txt2 . "</p>";
echo $x + $y;
?>
```

## The PHP print Statement

The print statement can be used with or without 
parentheses: 
print or print().

Display TextThe following example shows how to output text with the print 
command (notice that the text can contain HTML markup):

```
<?php
print "<p>Q: Why did Ford Prefect bring a towel?<br/>";
print "A: Why would he not?</p>";
?>
```

The following example shows how to output text and variables with the 
print statement:

```
<?php
$txt1 = "Tarzan";
$txt2 = "Jane";
$x = 5;
$y = 4;
print "<p>" . $txt1 . "<br/>";
print "loves " . $txt2 . "</p>";
print $x + $y;
?>
```
