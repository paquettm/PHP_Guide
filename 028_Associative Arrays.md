


# PHP Associative Arrays




## PHP Associative Arrays


Associative arrays are arrays that use named keys that you assign to them.


There are two ways to create an associative array: 


```

$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");```or:


```

$age['Peter'] = "35";
$age['Ben'] = "37";
$age['Joe'] = "43"; 
```The named keys can then be used in a script:```
<?php

$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
echo "Peter is " . $age['Peter'] . " years old.";
?>
```

## Loop Through an Associative Array


To loop through and print all the values of an associative array, you could use a foreach loop, like this:

```
 <?php$age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
foreach($age as $x => $x_value) {  echo "Key=" . $x . ", Value=" . $x_value;  echo "<br>";}?>
```## Complete PHP Array Reference


For a complete reference of all array functions, go to our complete PHP Array Reference.

[PHP Array Reference](php_ref_array.asp)The reference contains a brief description, and examples of use, for each function!
## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Create an associative array containing the age of Peter, Ben and Joe.