


# PHP Filters




Validating data = Determine if the data is in proper form.


Sanitizing data = Remove any illegal character from the data.
## The PHP Filter Extension 


PHP filters are used to validate and sanitize external input.


The PHP filter extension has many of the functions needed for checking user input,
and is designed to make data validation easier and quicker.


The filter_list() function can be used to list what the PHP filter extension offers: 

```
 <table>  <tr>    <td>Filter Name</td>    <td>Filter ID</td>  </tr>  <?php  foreach (filter_list() as $id =>$filter) {
      echo '<tr><td>' . $filter . '</td><td>' . filter_id($filter) . '</td></tr>';  }  ?></table> ```


## Why Use Filters?


Many web applications receive external input. External input/data can be:
* User input from a form


* Cookies


* Web services data


* Server variables


* Database query results

You should always validate external data!Invalid submitted data can lead to security problems and break your webpage!
By using PHP filters you can be sure your application gets the correct input!You should always validate external data!Invalid submitted data can lead to security problems and break your webpage!
By using PHP filters you can be sure your application gets the correct input!
## PHP filter_var() Function


The filter_var() function both validate and sanitize data.

The filter_var() function filters a single variable with a specified filter. It takes two pieces of data:* The variable you want to check


* The type of check to use

## Sanitize a String


The following example uses the filter_var() function to remove all HTML tags 
from a string:

```
 <?php$str = "<h1>Hello World!</h1>";$newstr = filter_var($str, FILTER_SANITIZE_STRING);echo $newstr;?>
```



## Validate an Integer


The following example uses the filter_var() function to check if the variable $int 
is an integer. If $int is an integer,
the output of the code below will be: "Integer is valid". If $int is not an integer, 
the output will be: "Integer is not valid":

```
 <?php$int = 100;if (!filter_var($int, FILTER_VALIDATE_INT) === false) {
    echo("Integer is valid");} else {  echo("Integer is not valid");}?>
```


In the example above, if $int was set to 0, the function above will return 
"Integer is not valid". To solve this problem, use the code below:```
 <?php$int = 0;if (filter_var($int, FILTER_VALIDATE_INT) === 0 || !filter_var($int, FILTER_VALIDATE_INT) === false) {
    echo("Integer is valid");} else {  echo("Integer is not valid");}?>
```

## Validate an IP Address


The following example uses the filter_var() function to check if the variable $ip 
is a valid IP address:

```
 <?php$ip = "127.0.0.1";if (!filter_var($ip, FILTER_VALIDATE_IP) === false) {
    echo("$ip is a valid IP address");} else {  echo("$ip is not a valid IP address");}?>
```

## Sanitize and Validate an Email Address


The following example uses the filter_var() function to first remove all 
illegal characters from the $email variable, then check if it 
is a valid email address:

```
 <?php$email = "john.doe@example.com";// Remove all illegal characters from email$email = filter_var($email, FILTER_SANITIZE_EMAIL);// Validate e-mailif (!filter_var($email, FILTER_VALIDATE_EMAIL) === false) {  echo("$email is a valid email address");} else {  echo("$email is not a valid email address");}?>
```




## Sanitize and Validate a URL


The following example uses the filter_var() function to first remove all 
illegal characters from a URL, then check if $url is a valid URL:

```
 <?php$url = "https://cstutoring.ca";
// Remove all illegal characters from a url$url = filter_var($url, FILTER_SANITIZE_URL);// Validate urlif (!filter_var($url, FILTER_VALIDATE_URL) === false) {  echo("$url is a valid URL");} else {  echo("$url is not a valid URL");}?>
```

## Complete PHP Filter Reference


For a complete reference of all filter functions, go to our complete
PHP Filter Reference. Check each filter to see 
what options and flags are available.

[PHP Filter Reference.](php_ref_filter.asp)The reference contains a brief description, and examples of use, for each function!


