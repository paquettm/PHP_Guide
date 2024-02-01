


# PHP File Handling




File handling is an important part of any web application. You 
often need to open and process a file for different tasks.
## PHP Manipulating Files


PHP has several functions for creating, reading, uploading, and editing files.
Be careful when manipulating files!When you are manipulating files you must be very careful. 
You can do a 
lot of damage if you do something wrong. Common errors are: editing the wrong 
file, filling a hard-drive with garbage data, and deleting the content of a file 
by accident.


Be careful when manipulating files!You can do a 
lot of damage if you do something wrong. Common errors are: editing the wrong 
file, filling a hard-drive with garbage data, and deleting the content of a file 
by accident.

## PHP readfile() Function


The readfile() function reads a file and writes it to the output buffer.

Assume we have a text file called "webdictionary.txt", stored on the 
server, that looks like this:


```
 AJAX = Asynchronous JavaScript and XMLCSS = Cascading Style Sheets
 HTML = Hyper Text Markup LanguagePHP = PHP Hypertext PreprocessorSQL = Structured Query LanguageSVG = Scalable Vector GraphicsXML = EXtensible Markup Language
```
The PHP code to read the file and write it to the output buffer is as follows 
(the readfile() function returns the number of bytes read on success):

```
 <?phpecho readfile("webdictionary.txt");?>
```

The readfile() function is useful if all you want to do is open up a file and read its contents.

The next chapters will teach you more about file handling.


## Exercise:


Assume we have a file named "webdict.txt", write the correct syntax to open and read the file content.