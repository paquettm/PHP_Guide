


# PHP Multidimensional Arrays




In the previous pages, we have described arrays that are a 
single list of key/value pairs.


However, sometimes you want to store values with more than one 
key. For this, we have multidimensional arrays.
## PHP - Multidimensional Arrays


A multidimensional array is an array containing one or more arrays.


PHP supports multidimensional arrays that are two, three, four, five, or 
more levels deep. However, arrays more than three levels deep are hard to manage for most people.
The dimension of an array indicates the number of indices you need to select an element.* For a two-dimensional array you need two indices to select an element


* For a three-dimensional array you need three indices to select an element

## PHP - Two-dimensional Arrays


A two-dimensional array is an array of arrays (a three-dimensional array is an array of arrays of arrays).


First, take a look at the following table:


We can store the data from the table above in a two-dimensional array, like this:


```
 $cars = array (  array("Volvo",22,18),  array("BMW",15,13),  array("Saab",5,2),  array("Land Rover",17,15));```
Now the two-dimensional $cars array contains four arrays, and it has two indices: row and column.


To get access to the elements of the $cars array we must point to the two 
indices (row and column):```
 <?phpecho $cars[0][0].": In stock: ".$cars[0][1].", sold: ".$cars[0][2].".<br>";echo $cars[1][0].": In stock: ".$cars[1][1].", sold: ".$cars[1][2].".<br>";echo $cars[2][0].": In stock: ".$cars[2][1].", sold: ".$cars[2][2].".<br>";echo $cars[3][0].": In stock: ".$cars[3][1].", sold: ".$cars[3][2].".<br>";?>```We can also put a for loop inside another for loop to get the elements of the 
$cars array (we still have to point to the two indices):
```
 <?phpfor ($row = 0; $row < 4; $row++) {  echo "<p><b>Row number $row</b></p>";  echo "<ul>";  for ($col = 0; $col < 3; $col++) {    echo "<li>".$cars[$row][$col]."</li>";  }  echo "</ul>";}?>```




## Complete PHP Array Reference


For a complete reference of all array functions, go to our complete PHP Array Reference.

[PHP Array Reference](php_ref_array.asp)The reference contains a brief description, and examples of use, for each function!


