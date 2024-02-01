


# PHP - AJAX and PHP




AJAX is used to create more interactive applications.
## AJAX PHP Example


The following example will demonstrate how a web page can communicate with a 
web server while a user type characters in an input field:
Start typing a name in the input field below:


Suggestions: ## Example Explained


In the example above, when a user types a character in the input field, a function 
called "showHint()" is executed.


The function is triggered by the onkeyup event.


Here is the HTML code:```
 <html><head><script>function showHint(str) {  if (str.length == 0) { 
      document.getElementById("txtHint").innerHTML = "";    return;  } else {    var xmlhttp = new XMLHttpRequest();    xmlhttp.onreadystatechange = function() {      if (this.readyState == 4 && this.status == 200) {        document.getElementById("txtHint").innerHTML = this.responseText;      }    };    xmlhttp.open("GET", "gethint.php?q=" + str, true);    xmlhttp.send();
    }}</script></head><body><p><b>Start typing a name in the input field below:</b></p>
  <form action="">  <label for="fname">First name:</label>  
  <input type="text" id="fname" name="fname" onkeyup="showHint(this.value)">
  </form><p>Suggestions: <span id="txtHint"></span></p>
 </body></html>```

Code explanation:


First, check if the input field is empty (str.length == 0). If it is, clear the 
content of the txtHint placeholder and exit the function.


However, if the input field is not empty, do the following:
* Create an XMLHttpRequest object


* Create the function to be executed when the server response is ready


* Send the request off to a PHP file (gethint.php) on the server


* Notice that q parameter is added to the url (gethint.php?q="+str)


* And the str variable holds the content of the input field## The PHP File - "gethint.php"


The PHP file checks an array of names, and returns the corresponding name(s) to the 
browser:
```
<?php
// Array with names
$a[] = "Anna";
$a[] = "Brittany";
$a[] = "Cinderella";
$a[] = "Diana";
$a[] = "Eva";
$a[] = "Fiona";
$a[] = "Gunda";
$a[] = "Hege";
$a[] = "Inga";
$a[] = "Johanna";
$a[] = "Kitty";
$a[] = "Linda";
$a[] = "Nina";
$a[] = "Ophelia";
$a[] = "Petunia";
$a[] = "Amanda";
$a[] = "Raquel";
$a[] = "Cindy";
$a[] = "Doris";
$a[] = "Eve";
$a[] = "Evita";
$a[] = "Sunniva";
$a[] = "Tove";
$a[] = "Unni";
$a[] = "Violet";
$a[] = "Liza";
$a[] = "Elizabeth";
$a[] = "Ellen";
$a[] = "Wenche";
$a[] = "Vicky";
 // get the q parameter from URL$q = $_REQUEST["q"];$hint = "";// lookup all hints from array if $q is different from "" if ($q !== "") {  $q = strtolower($q);  $len=strlen($q);  foreach($a as $name) {    if (stristr($q, substr($name, 0, $len))) {      if ($hint === "") {        $hint = $name;      } else {        $hint .= ", $name";      }
     }  }}// Output "no suggestion" if no hint was found or output correct values 
 echo $hint === "" ? "no suggestion" : $hint;?>
```
