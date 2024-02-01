


# PHP File Create/Write




In this chapter we will teach you how to create and write to a file 
on the server.
## PHP Create File - fopen()


The fopen() function is also used to create a file. Maybe a little confusing, but in PHP, a file is created using the same 
function used to open files.

If you use fopen() on a file that does not 
exist, it will create it, given that the file is opened for writing (w) or 
appending (a).

The example below creates a new file called "testfile.txt". The file will be 
created in the same directory where the PHP code resides:```
 $myfile = fopen("testfile.txt", "w")
```## PHP File Permissions


If you are having errors when trying to get this code to run, check that you have granted your PHP file access to write 
information to the hard drive.
## PHP Write to File - fwrite()


The fwrite() function is used to write to a file.

The first parameter of fwrite() contains the name of the file to write to and 
the second parameter is the string to be written.

The example below writes a couple of names into a new file called "newfile.txt":```
 <?php$myfile = fopen("newfile.txt", "w") or die("Unable to open file!");$txt = "John Doe\n";fwrite($myfile, $txt);$txt = "Jane Doe\n";fwrite($myfile, $txt);fclose($myfile);?>
```

Notice that we wrote to the file "newfile.txt" twice. Each time we wrote to 
the file we sent the string $txt that first contained "John Doe" and second 
contained "Jane Doe". After we finished writing, we closed the file using the fclose() function.

If we open the "newfile.txt" file it would look like this:


```
 John DoeJane Doe
```

## PHP Overwriting


Now that "newfile.txt" contains some data we can show what happens when we 
open an existing file for writing. All the existing data will be ERASED and we 
start with an empty file.


In the example below we open our existing file "newfile.txt", and write some 
new data into it:```
 <?php$myfile = fopen("newfile.txt", "w") or die("Unable to open file!");$txt = "Mickey Mouse\n";fwrite($myfile, $txt);$txt = "Minnie Mouse\n";fwrite($myfile, $txt);fclose($myfile);?>
```

If we now open the "newfile.txt" file, both John and Jane have 
vanished, and only the data we just wrote is present:


```
 Mickey MouseMinnie Mouse
```## PHP Append Text


You can append data to a file by using the "a" mode. The "a" mode appends 
text to the end of the file, while the "w" mode overrides (and erases) the old 
content of the file.


In the example below we open our existing file "newfile.txt", and 
append some text to it:```
 <?php$myfile = fopen("newfile.txt", "a") or die("Unable to open file!");$txt = "Donald 
  Duck\n";fwrite($myfile, $txt);$txt = "Goofy Goof\n";fwrite($myfile, $txt);fclose($myfile);?>
```

If we now open the "newfile.txt" file, we will see that Donald Duck 
and Goofy Goof is appended to the end of the file:


```
 Mickey MouseMinnie MouseDonald DuckGoofy Goof
```## Complete PHP Filesystem Reference


For a complete reference of filesystem functions, go to our complete
PHP Filesystem Reference.

[PHP Filesystem Reference](php_ref_filesystem.asp)