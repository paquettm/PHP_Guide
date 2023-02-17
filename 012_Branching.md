# if...else...elseif Statements

Conditional statements are used to perform different actions based on different conditions.
## PHP Conditional Statements


Very often when you write code, you want to perform different actions for 
different conditions. You can use conditional statements in your code to do this.


In PHP we have the following conditional statements:
* if statement - executes some code if one condition is true
* if...else statement - executes some code if a condition is true and another code if that condition is false
* if...elseif...else statement  - executes different codes for more than two conditions
* switch statement - selects one of many blocks of code to be executed## PHP - The if Statement


The if statement executes some code if one condition is true.```
if (condition) {
    code to be executed if condition is true;}
```Output "Have a good day!" if the current time (HOUR) is less than 20:


```
<?php
$t = date("H");
if ($t < "20") {
  echo "Have a good day!";
 }
?>
```

## PHP - The if...else Statement


The if...else statement executes some code if a condition is true and 
another code if that condition is false.```
if (condition) {
    code to be executed if condition is true;
 }
else {
  code to be executed if condition is false;
}
```


Output "Have a good day!" if the current time is less than 20, and "Have a 
  good night!" otherwise:


```
<?php
$t = date("H");
if ($t < "20") {
 
echo "Have a good day!";
 }
else {
  echo 
"Have a good night!";
 }
?>
```

## PHP - The if...elseif...else Statement


The if...elseif...else statement executes different codes for more than two 
conditions.```
if (condition) {
    code to be executed if this condition is true;
}
elseif (condition) {
    code to be executed if first condition is false and this 
  condition is true;
} else {
  code to be executed if all conditions are false;
}
```Output "Have a good morning!" if the current time is less than 10, and 
  "Have a good day!" if the current time is less than 20. Otherwise it will 
  output "Have a good night!":


```
<?php
$t = date("H");
if ($t < "10") {
  echo "Have a good morning!";
 }
elseif ($t < "20") {
    echo "Have a good day!";
 } else {
  echo "Have a good night!";
 }
?>
```


## PHP - The switch Statement




# PHP switch Statement

The switch statement is used to perform different actions based on different conditions.## The PHP switch Statement


Use the switch statement to select one of many blocks 
of code to be executed.


```

switch (n)
{
  case label1:
    code to be executed if n=label1;
      break;
 
case label2:
    code to be executed if n=label2;
   
break;
 
case label3:
    code to be executed if n=label3;
   
break;    ...
  default:
    code to be executed if n is different from all labels;
}

```

This is how it works: First we have a single expression n (most often a
variable), that is evaluated once. The value of the expression is then compared
with the values for each case in the structure. If there is a match, the block
of code associated with that case is executed. Use break to prevent the
code from running into the next case automatically. The default statement is used if no 
match is found.```
 <?php
 $favcolor = "red";
 switch ($favcolor)
 {
   case "red":
      echo "Your favorite color is red!";
      break;
  
 case "blue":
      echo "Your favorite color is blue!";
      break;
  
 case "green":
     echo "Your favorite color is green!";
    
 break;
  
 default:
      echo "Your favorite color is neither red, blue, nor green!";
 }
 ?>
```


## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Create a switch statement that will output "Hello"
if $color is "red", and "welcome"
if $color is "green".

The switch statement will be explained in the next chapter.## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Output "Hello World" if $a is greater than $b.
