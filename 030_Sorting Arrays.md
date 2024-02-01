


# PHP Sorting Arrays




The elements in an array can be sorted in alphabetical or numerical order, descending or ascending.
## PHP - Sort Functions For Arrays


In this chapter, we will go through the following PHP array sort functions:
* sort() - sort arrays in ascending order
* rsort() - sort arrays in descending order
* asort() - sort associative arrays in ascending order, according to the value
* ksort() - sort associative arrays in ascending order, according to the key
* arsort() - sort associative arrays in descending order, according to the value
* krsort() - sort associative arrays in descending order, according to the key## Sort Array in Ascending Order - sort()


The following example sorts the elements of the $cars array in ascending alphabetical order:```
<?php
 $cars = array("Volvo", "BMW", "Toyota");sort($cars);?>
```The following example sorts the elements of the $numbers array in ascending 
numerical order:```
<?php
 $numbers = array(4, 6, 2, 22, 11);sort($numbers);?>
```## Sort Array in Descending Order - rsort()


The following example sorts the elements of the $cars array in descending alphabetical order:```
<?php
 $cars = array("Volvo", "BMW", "Toyota");rsort($cars);?>
```The following example sorts the elements of the $numbers array in descending 
numerical order:```
<?php
 $numbers = array(4, 6, 2, 22, 11);rsort($numbers);?>
```

## Sort Array (Ascending Order), According to Value - asort()


The following example sorts an associative array in ascending order, 
according to the value:```
<?php
 $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
 asort($age);?>
```

## Sort Array (Ascending Order), According to Key - ksort()


The following example sorts an associative array in ascending order, 
according to the key:```
<?php
 $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
 ksort($age);?>
```

## Sort Array (Descending Order), According to Value - arsort()


The following example sorts an associative array in descending order, 
according to the value:```
<?php
 $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
 arsort($age);?>
```

## Sort Array (Descending Order), According to Key - krsort()


The following example sorts an associative array in descending order, 
according to the key:```
<?php
 $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
 krsort($age);?>
```

## Complete PHP Array Reference


For a complete reference of all array functions, go to our complete PHP Array Reference.

[PHP Array Reference](php_ref_array.asp)The reference contains a brief description, and examples of use, for each function!
## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Use the correct array method to sort the $colors array alphabetically.


