


# PHP Filters Advanced




## Validate an Integer Within a Range


The following example uses the filter_var() function to check if a variable 
is both of type INT, and between 1 and 200:

```
 <?php$int = 122;$min = 1;$max = 200;if (filter_var($int, FILTER_VALIDATE_INT, array("options" => array("min_range"=>$min, "max_range"=>$max))) === false) {  echo("Variable value is not within the legal range");} else {  echo("Variable value is within the legal range");}?>
```

## Validate IPv6 Address


The following example uses the filter_var() function to check if the variable $ip is a valid 
IPv6 address:

```
 <?php$ip = "2001:0db8:85a3:08d3:1319:8a2e:0370:7334";if (!filter_var($ip, FILTER_VALIDATE_IP, FILTER_FLAG_IPV6) === false) {  echo("$ip is a valid IPv6 address");} else {
    echo("$ip is not a valid IPv6 address");}?>
```## Validate URL - Must Contain QueryString


The following example uses the filter_var() function to check if the variable $url is a 
URL with a querystring:

```
 <?php$url = "https://cstutoring.ca";if (!filter_var($url, FILTER_VALIDATE_URL, FILTER_FLAG_QUERY_REQUIRED) === false) {  echo("$url is a valid URL with a query string");} else {
    echo("$url is not a valid URL with a query string");}?>
```

## Remove Characters With ASCII Value > 127


The following example uses the filter_var() function to sanitize a string. It 
will both remove all HTML tags, and all characters with ASCII value > 127, from 
the string:

```
 <?php$str = "<h1>Hello WorldÃÃÃ!</h1>";$newstr = filter_var($str, FILTER_SANITIZE_STRING, FILTER_FLAG_STRIP_HIGH);echo $newstr;?>
```




## Complete PHP Filter Reference


For a complete reference of all filter functions, go to our complete
PHP Filter Reference. Check each filter to see 
what options and flags are available.

[PHP Filter Reference.](php_ref_filter.asp)The reference contains a brief description, and examples of use, for each function!


