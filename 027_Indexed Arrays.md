


# PHP Indexed Arrays




## PHP Indexed Arrays


There are two ways to create indexed arrays:


The index can be assigned automatically (index 
always starts at 0), like this:


```
$cars = array("Volvo", "BMW", "Toyota");```or the index can be assigned manually:


```
$cars[0] = "Volvo";
$cars[1] = "BMW";
$cars[2] = "Toyota";
```The following example creates an indexed array named $cars, assigns three 
elements to it, and then prints a text containing the array values:```
<?php
 $cars = array("Volvo", "BMW", "Toyota");echo "I like " . $cars[0] . ", " . $cars[1] . " and " . $cars[2] . ".";
?>
```

## Loop Through an Indexed Array


To loop through and print all the values of an indexed array, you could use a for loop, like this:

```
<?php
 $cars = array("Volvo", "BMW", "Toyota");
 $arrlength = count($cars);for($x = 0; $x < $arrlength; $x++) {  echo $cars[$x];  echo "<br>";}?>
```## Complete PHP Array Reference


For a complete reference of all array functions, go to our complete PHP Array Reference.

[PHP Array Reference](php_ref_array.asp)The reference contains a brief description, and examples of use, for each function!
## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Output the second item in the $fruits array.