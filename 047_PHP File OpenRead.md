


# PHP File Open/Read/Close




In this chapter we will teach you how to open, read, and close a file 
on the server.
## PHP Open File - fopen()


A better method to open files is with the fopen() function. This function gives you more 
options than the readfile() function.We will use the text file, "webdictionary.txt", during the lessons:


```
 AJAX = Asynchronous JavaScript and XMLCSS = Cascading Style Sheets
 HTML = Hyper Text Markup LanguagePHP = PHP Hypertext PreprocessorSQL = Structured Query LanguageSVG = Scalable Vector GraphicsXML = EXtensible Markup Language
```
The first parameter of fopen() contains the name of the file to be opened and the 
second parameter specifies in which mode the file should be opened. The following example 
also generates a message if the fopen() function is unable to open the specified file:

```
 <?php
    $myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");echo fread($myfile,filesize("webdictionary.txt"));
 fclose($myfile);?>
```

Tip: The fread() and the fclose() functions will be 
explained below.

The file may be opened in one of the following modes:## PHP Read File - fread()


The fread() function reads from an open file.

The first parameter of fread() contains the name of the file to read from and 
the second parameter specifies the maximum number of bytes to read.

The following PHP code reads the "webdictionary.txt" file to the end:


```
 fread($myfile,filesize("webdictionary.txt"));
 ```

## PHP Close File - fclose()


The fclose() function is used to close an open file.It's a good programming practice to close all files after you have finished with them. 
You don't want an open file running around on your 
server taking up resources!The fclose() requires the name of the file (or a variable that holds the 
filename) we want to close:

```

<?php
 $myfile = fopen("webdictionary.txt", "r");// some code to be executed....
 fclose($myfile);
?>
```

## PHP Read Single Line - fgets()


The fgets() function is used to read a single line from a file.

The example below outputs the first line of the "webdictionary.txt" file:```
 <?php$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");echo fgets($myfile);
 fclose($myfile);?>
```

Note: After a call to the fgets() function, the file pointer has moved to the next line.
## PHP Check End-Of-File - feof()


The feof() function checks if the "end-of-file" (EOF) has been reached.

The feof() function is useful for looping through data of unknown length.

The example below reads the "webdictionary.txt" file line by line, until end-of-file is reached:```
 <?php$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");// Output one line until end-of-filewhile(!feof($myfile)) {  echo fgets($myfile) . "<br>";}fclose($myfile);?>
```

## PHP Read Single Character - fgetc()


The fgetc() function is used to read a single character from a file.

The example below reads the "webdictionary.txt" file character by 
character, until end-of-file is reached:```
 <?php$myfile = fopen("webdictionary.txt", "r") or die("Unable to open file!");// Output one character until end-of-filewhile(!feof($myfile)) {  echo fgetc($myfile);}fclose($myfile);?>
```
Note: After a call to the fgetc() function, the file pointer moves to the next character.
## Complete PHP Filesystem Reference


For a complete reference of filesystem functions, go to our complete
PHP Filesystem Reference.

[PHP Filesystem Reference](php_ref_filesystem.asp)

## PHP Exercises
## Test Yourself With Exercises
## Exercise:


Open a file, and write the correct syntax to output one character at the time, until end-of-file.

