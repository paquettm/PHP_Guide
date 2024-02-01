


# PHP SimpleXML Parser




SimpleXML is a PHP extension that allows us to easily 
manipulate and get XML data.
## The SimpleXML Parser


SimpleXML is a tree-based parser.


SimpleXML provides an easy way of getting an element's name, attributes and textual 
content if you know the XML document's structure or layout.


SimpleXML turns an XML document into a data structure you can iterate through 
like a collection of arrays and objects.


Compared to DOM or the Expat parser, SimpleXML takes a fewer lines of code to 
read text data from an element.
## Installation


From PHP 5, the SimpleXML functions are part of the PHP core. No installation is required to use these functions.
## PHP SimpleXML - Read From String


The PHP simplexml_load_string() function is used to read XML data from a string.

Assume we have a variable that contains XML data, like this:
```
$myXMLData = "<?xml version='1.0' encoding='UTF-8'?>
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>";
```The example below shows how to use the simplexml_load_string() function to 
read XML data from a string:

```
<?php$myXMLData ="<?xml version='1.0' encoding='UTF-8'?>
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>";
$xml=simplexml_load_string($myXMLData) or die("Error: Cannot create object");print_r($xml);
?>
```The output of the code above will be:


```
 SimpleXMLElement Object ( [to] => Tove [from] => Jani [heading] => Reminder [body] => Don't forget me this weekend! )
```Error Handling Tip: Use the libxml functionality to retrieve 
all XML errors when loading the document and then iterate over the errors. The 
following example tries to load a broken XML string:
```
<?phplibxml_use_internal_errors(true);$myXMLData ="<?xml version='1.0' encoding='UTF-8'?> <document> <user>John Doe</wronguser> <email>john@example.com</wrongemail>
 </document>"; $xml = simplexml_load_string($myXMLData);if ($xml === false) {
    echo "Failed loading XML: ";  foreach(libxml_get_errors() as $error) {    echo "<br>", $error->message;
    }} else {  print_r($xml);}
?>
```

The output of the code above will be:


```
 Failed loading XML: Opening and ending tag mismatch: user line 3 and wronguserOpening and ending tag mismatch: email line 4 and wrongemail
```


## PHP SimpleXML - Read From File


The PHP simplexml_load_file() function is used to read XML data from a file.

Assume we have an XML file called "note.xml", 
that looks like this:

[note.xml](note.xml)

```
<?xml version="1.0" encoding="UTF-8"?>
<note>
 
<to>Tove</to>
 
<from>Jani</from>
 
<heading>Reminder</heading>
 
<body>Don't forget me this weekend!</body>
</note>
```

The example below shows how to use the simplexml_load_file() function to read 
XML data from a file:

```
<?php
$xml=simplexml_load_file("note.xml") or die("Error: Cannot create object");
 print_r($xml);
?>
```The output of the code above will be:


```
 SimpleXMLElement Object ( [to] => Tove [from] => Jani [heading] => Reminder [body] => Don't forget me this weekend! )
```Tip: The next chapter shows how to get/retrieve node values 
from an XML file with SimpleXML!


## More PHP SimpleXML


For more information about the PHP SimpleXML functions, visit our
PHP SimpleXML Reference.

[PHP SimpleXML Reference](php_ref_simplexml.asp)