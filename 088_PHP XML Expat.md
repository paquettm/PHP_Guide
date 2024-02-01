


# PHP XML Expat Parser




The built-in XML Expat Parser makes it possible to process XML 
documents in PHP.
## The XML Expat Parser


The Expat parser is an event-based parser.


Look at the following XML fraction:


```

<from>Jani</from>

```An event-based parser reports the XML above as a series of three events: 
* Start element: from


* Start CDATA section, value: Jani


* Close element: fromThe XML Expat Parser functions are part of the PHP core. There is no 
installation needed to use these functions.
## The XML File


The XML file "note.xml" will be used in the example below:


```

<?xml version="1.0" encoding="UTF-8"?>
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>

```

## Initializing the XML Expat Parser


We want to initialize the XML Expat Parser in PHP, define some handlers for different 
XML events, and then parse the XML file.```
<?php
// Initialize the XML parser
$parser=xml_parser_create();

// Function to use at the start of an element
function start($parser,$element_name,$element_attrs) {
  switch($element_name) {
    case "NOTE":
    echo "-- Note --<br>";
    break;
    case "TO":
    echo "To: ";
    break;
    case "FROM":
    echo "From: ";
    break;
    case "HEADING":
    echo "Heading: ";
    break;
    case "BODY":
    echo "Message: ";
   }
 }

// Function to use at the end of an element
function stop($parser,$element_name) {
  echo "<br>";
 }

// Function to use when finding character data
function char($parser,$data) {
  echo $data;
 }

// Specify element handler
xml_set_element_handler($parser,"start","stop");

// Specify data handler
xml_set_character_data_handler($parser,"char");

// Open XML file
$fp=fopen("note.xml","r");

// Read data
while ($data=fread($fp,4096)) {
  xml_parse($parser,$data,feof($fp)) or 
  die (sprintf("XML Error: %s at line %d", 
  xml_error_string(xml_get_error_code($parser)),
  xml_get_current_line_number($parser)));
 }

// Free the XML parser
xml_parser_free($parser);
?>
```
Example explained:
* Initialize the XML parser with the xml_parser_create() function

* Create functions to use with the different event handlers


* Add the xml_set_element_handler() function to specify which function will be executed when the parser encounters the opening and closing tags

* Add the xml_set_character_data_handler() function to specify which function will execute when the parser encounters character data

* Parse the file "note.xml" with the xml_parse() function

* In case of an error, add xml_error_string() function to convert an XML error to a textual description

* Call the xml_parser_free() function to release the memory allocated with the xml_parser_create() function


## More PHP XML Expat Parser


For more information about the PHP Expat functions, visit our PHP XML Parser Reference.

[PHP XML Parser Reference](php_ref_xml.asp)