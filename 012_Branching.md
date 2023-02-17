# Branching

As part of possible code control, there are structures that enforce the conditional execution of code. This is called branching and it is implemented with if..elseif..else amd switch statements.

Conditional statements are used to perform different actions based on different conditions.

Very often when you write code, you want to perform different actions for 
different conditions. You can use conditional statements in your code to do this.

In PHP we have the following conditional statements:
* if statement - executes some code if one condition is true
* if...else statement - executes some code if a condition is true and another code if that condition is false
* if...elseif...else statement  - executes different codes for more than two conditions
* switch statement - selects one of many blocks of code to be executed


## if Statement

The if statement executes some code if one condition is true.
```
if (condition) {
  //code to be executed if condition is true;
}
```

Output "Have a good day!" if the current time (HOUR) is less than 20:

```
<?php
$t = date("H");
if ($t < "20") {
  echo "Have a good day!";
}
?>
```

## if...else Statement

By adding an else branch to the if statement, we can define what happens in the case when the condition in the if statement is false.
```
if (condition){
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
}else {
  echo "Have a good night!";
}
?>
```

## The if...elseif...else Statement

When the code to run is to be determined following a prioritized list of conditions, then we use the if..elseif..else statement. In other words, by adding elseif statements after the if statement and before the else branch, we can define code to run **if a secondary conditions is satisfied and all preceding conditions are not satisfied**. 
```
if (condition1) {
  code to be executed if this condition1 is true;
}elseif (condition2) {
  code to be executed if condition1 is false and condition2 is true;
}elseif (condition3) {
  code to be executed if condition1 and condition2 are false and condition3 is true;
}elseif (condition4) {
  code to be executed if condition1, condition2, and condition3 are false and condition4 is true;
} else {
  code to be executed if all conditions are false;
}
```

Output "Have a good morning!" if the current time is less than 10, and 
  "Have a good day!" if the current time is less than 20. Otherwise it will 
  output "Have a good night!":

```
<?php
$t = date("H");
if ($t < "10") {
  echo "Have a good morning!";
}elseif ($t < "20") {
  echo "Have a good day!";
} else {
  echo "Have a good night!";
}
?>
```

## The switch Statement

The switch statement is used to perform different actions based on different **values**.

Use the switch statement to select one of many blocks of code to be executed (or select the entry label within a block of code to run).

```
switch (expression)
{
  case 'label1':
    //code to be executed if expression=='label1';
    break;
  case 'label2':
    //code to be executed if expression=='label2';
    break;
  case 'label3':
    //code to be executed if expression=='label3';
    break;
    //...
  default:
    //code to be executed if expression is different from all labels;
}
```

This is how it works: First we have a single expression (most often a
variable), that is evaluated once. The value of the expression is then compared
with the values for each case in the structure. If there is a match, the block
of code associated with that case is executed. We use break to prevent the
code from the following cases to run (without break statements, all code placed below the entry label for this execution will be run). The default statement is used if no 
match is found.

```
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
