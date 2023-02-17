# Looping

Often when you write code, you want the same block of code to run multiple times.
We use loops, instead of adding almost identical code blocks to our programs.

Loops are control structures that allow the repetition of code while a condition is satisfied.

This allows us to write code that can process multiple elements of a collection of data, for example.

In PHP, we have the following loop types:
* while - as long as the specified condition is true, loops through a block of code 
* do...while - loops through a block of code, and then loops to the code as long as the specified condition is true (always runs the code at least once)
* for - loops through a block of code a specified number of times
* foreach - loops through a block of code for each element of an array

## while Loop

The while loop repeats a block of code as long as the specified condition is true.

Its syntax is as follows:
```
while (condition is true) {
  //code to be executed;
}
```

For example, the code below displays the numbers from 1 to 5:

```
<?php
$x = 1;
while($x <= 5) {
  echo "The number is: $x <br>";
  $x++;
} 
?>
```

In this example,
* `$x = 1;` initializes the **loop counter** `$x` to 1
* The condition `$x <= 5` is evaluated each time before running the code in the loop body and only runs it if the condition evaluates to `true`. In this case, the loop runs as long as `$x` is less than or equal to 5.
* `$x++;` increments the loop counter value by 1 at each iteration (repetition of the loop).

In general, for a while loop to be well written, you will need
* a condition that is related to the items modified in the loop body
* a change inside the loop that eventually renders th condition false
That is unless you want an _infinity loop_: a loop that runs forever.

The following example outputs numbers from 0 to 100 by tens:
```
<?php
$x = 0;
while($x <= 100) {
  echo "The number is: $x <br>";
  $x+=10;
}
?>
```

* $x = 0; - Initialize the loop counter ($x), and set the start value to 0
* $x <= 100 - Continue the loop as long as $x is less than or equal to 100 (This condition is related to something that changes in the body of the loop)
* $x+=10; - Increase the loop counter value by 10 for each iteration (This chang will eventually render the condition false)

## do..while  Loop

The do...while loop will run block of code once, and then repeat it as long as the specified 
condition is true.

```
do
{
  //code to be executed;
}while (condition);
```

The example below first sets a variable $x to 1 ($x = 1). Then, the do while 
loop will write some output, and then increment the variable $x with 1. Then the condition is checked (is 
$x less than, or equal to 5?), and the loop will continue to run as long as $x is less than, or equal to 5:
```
<?php
  $x = 1;
  do {
    echo "The number is: $x <br>";
    $x++;
}while ($x <= 5);
?>
```

Note: In a do...while loop the condition is tested AFTER executing 
the statements within the loop. This means that the do...while loop will execute 
its statements at least once, even if the condition is false. 
This type of loop is called post-condition loop as opposed to pre-condition in the case of the while loop.

To illustrate that do..while loops are indeed post-condition loops, the code in the following example sets the $x variable to 6, a value that renders the loop condition false from the beginning, however, the loop body is still run once before the condition is checked:

```
<?php
$x = 6;
do {
  echo "The number is: $x <br>";
  $x++;
} while ($x <= 5);
?>
```

## for Loop

The for loop repeats a block of code a specified number of times.

The for loop is used when you know in advance how many times the script should run.
```
for (counter initialization; condition on counter; counter change)
{
  code to be executed for each iteration;
}
```

Parameters:
* counter initialization: Initialize the loop counter value
* condition on counter: For each repetition, the code runs only if the condition evaluates to `true`. If it evaluates to `false`, the repetition ends.
* counter change: Increment or decrement the loop counter value depending on the purpose. This change is applied after the loop body runs.

The example below displays the numbers from 10 to 0:
```
<?php for ($x = 10; $x >= 0; $x--)
{
  echo "The number is: $x <br>";
}
?> 
```

* `$x = 10;` initializes the loop counter `$x` to 10.
* `$x >= 0;` runs the loop body as long as `$x` is greater than or equal to 0
* `$x--` decrements the loop counter value by 1 for each iteration


This example counts to 100 by tens:
```
<?php for ($x = 0; $x <= 100; $x+=10)
{
  echo "The number is: $x <br>";
}
?>
```

* `$x = 0;` initializes the loop counter `$x` to 0.
* `$x <= 100;` runs the loop body and repeat as long as `$x` is less than or equal to 100.
* `$x+=10` increases the loop counter value by 10 for each iteration (repetition)


## foreach Loop

The foreach loop repeats a block of code for each element in an array.

The foreach loop works only on arrays, and is used to loop through each key/value pair in an array.

```
foreach ($array as $value)
{
  code to be executed;
}
```

For every loop iteration, the value of the current array element is assigned to $value and the array pointer is moved by one, until it reaches the last array element.

The following example will output the values of the given array ($colors):
```
<?php
$colours = ['red', 'green', 'blue', 'yellow']; 
foreach ($colours as $colour) {
  echo "$colour <br>";
}
?>
```

The following example will output both the keys and the values of  the 
given array ($age):
```
<?php
$ages = ['Peter'=>'35', 'Ben'=>'37', 'Joe'=>'43'];
foreach($ages as $key => $value){
  echo "$key = $value<br>";
}
?>
```
