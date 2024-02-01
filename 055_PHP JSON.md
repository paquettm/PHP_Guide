


# PHP and JSON




## What is JSON?


JSON stands for JavaScript Object Notation, and is a syntax for storing and 
exchanging data.


Since the JSON format is a text-based format, it can easily be sent to and 
from a server, and used as a data format by any programming language.
## PHP and JSON


PHP has some built-in functions to handle JSON.


First, we will look at the following two functions:
* 
json_encode()
* 
json_decode() ## PHP - json_encode()


The json_encode() function is used to encode a value to JSON format.

This example shows how to encode an associative array into a JSON object:


```
  <?php$age = array("Peter"=>35, "Ben"=>37, "Joe"=>43);
echo json_encode($age);?>```


This example shows how to encode an indexed array into a JSON array:


```
  <?php$cars = array("Volvo", "BMW", "Toyota");echo json_encode($cars);?>```

## PHP - json_decode()


The json_decode() function is used to decode 
a JSON object into a PHP object or an associative array.

This example decodes JSON data into a 
PHP object:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';var_dump(json_decode($jsonobj));?>```

The json_decode() function returns an object 
by default. The json_decode() function has a 
second parameter, and when set to true, JSON objects are decoded into 
associative arrays.
This example decodes JSON data into a 
PHP 
associative array:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';var_dump(json_decode($jsonobj, 
  true));?>```



## PHP - Accessing the Decoded Values


Here are two examples of how to access the decoded values from an object and 
from an associative array:This example shows how to access the values from a PHP object:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
  $obj = json_decode($jsonobj);echo $obj->Peter;echo $obj->Ben;
  echo $obj->Joe;?>```This example shows how to access the values from a 
PHP associative array:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
  $arr = json_decode($jsonobj, true);echo $arr["Peter"];echo $arr["Ben"];
  echo $arr["Joe"];?>```

## PHP - Looping Through the Values


You can also loop through the values with a foreach() 
loop:

This example shows how to loop through the values of a PHP object:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
  $obj = json_decode($jsonobj);foreach($obj 
  as $key => $value) {  echo $key . " => " . $value . "<br>";}?>```This example shows how to loop through the 
values of a PHP associative array:


```
  <?php$jsonobj = '{"Peter":35,"Ben":37,"Joe":43}';
  $arr = json_decode($jsonobj, true);foreach($arr as $key => $value) {  echo $key . " => " . $value 
  . "<br>";}?>```