


# PHP SimpleXML - Get Node/Attribute Values




SimpleXML is a PHP extension that allows us to easily 
manipulate and get XML data.
## PHP SimpleXML - Get Node Values


Get the node values from the "note.xml" file:

[note.xml](note.xml)```
 <?php$xml=simplexml_load_file("note.xml") or die("Error: Cannot create object");echo $xml->to . "<br>";
 echo $xml->from . "<br>";echo $xml->heading . "<br>";echo $xml->body;?>
```

The output of the code above will be:


```
Tove
Jani
Reminder
Don't forget me this weekend!
```


## Another XML File


Assume we have an XML file called "books.xml", 
that looks like this: 

[books.xml](books.xml)```
 <?xml version="1.0" encoding="utf-8"?><bookstore>  <book category="COOKING">    <title lang="en">Everyday Italian</title>    <author>Giada De Laurentiis</author>    <year>2005</year>
    
 <price>30.00</price>  </book>  <book category="CHILDREN">    <title lang="en">Harry Potter</title>    <author>J K. Rowling</author>    <year>2005</year>
    
 <price>29.99</price>  </book>  <book category="WEB">    <title lang="en-us">XQuery Kick Start</title>    <author>James McGovern</author>    <year>2003</year>    <price>49.99</price>  </book>
  
 <book category="WEB">    <title lang="en-us">Learning XML</title>
    
 <author>Erik T. Ray</author>
    
 <year>2003</year>    <price>39.95</price>  </book></bookstore>
```

## PHP SimpleXML - Get Node Values of Specific Elements


The following example gets the node value of the <title> element in the first 
and second <book> elements in the "books.xml" file: ```
 <?php$xml=simplexml_load_file("books.xml") or die("Error: Cannot create object");echo $xml->book[0]->title . "<br>";echo $xml->book[1]->title; ?>
```

The output of the code above will be:


```
 Everyday ItalianHarry Potter
```## PHP SimpleXML - Get Node Values - Loop


The following example loops through all the <book> elements in the "books.xml" file, 
and gets the node values of the <title>, <author>, <year>, and <price> elements:```
 <?php$xml=simplexml_load_file("books.xml") or die("Error: Cannot create object");foreach($xml->children() as $books) {   echo $books->title . ", "; 
    echo $books->author . ", ";   echo $books->year . ", ";
    echo $books->price . "<br>"; } ?>
```
The output of the code above will be:


```
 Everyday Italian, Giada De Laurentiis, 2005, 30.00Harry Potter, J K. Rowling, 2005, 29.99XQuery Kick Start, James McGovern, 2003, 49.99
 Learning XML, Erik T. Ray, 2003, 39.95
```


## PHP SimpleXML - Get Attribute Values


The following example gets the attribute value of the "category" attribute of 
the first <book> element and the attribute value of the "lang" attribute 
of the <title> element in the second <book> element:```
 <?php$xml=simplexml_load_file("books.xml") or die("Error: Cannot create object");echo $xml->book[0]['category'] . "<br>";echo $xml->book[1]->title['lang']; ?>
```

The output of the code above will be:


```
 COOKINGen
 ```
 ## PHP SimpleXML - Get Attribute Values - Loop


The following example gets the attribute values of the <title> elements in the "books.xml" file:```
 <?php$xml=simplexml_load_file("books.xml") or die("Error: Cannot create object");foreach($xml->children() as $books) {   echo $books->title['lang'];
    echo "<br>"; } ?>
```

The output of the code above will be:


```
enenen-usen-us```


## More PHP SimpleXML


For more information about the PHP SimpleXML functions, visit our
PHP SimpleXML Reference.

[PHP SimpleXML Reference](php_ref_simplexml.asp)