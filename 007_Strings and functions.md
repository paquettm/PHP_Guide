# Strings and String Functions

A string is a sequence of characters, like "Hello world!".

## PHP String Functions

In this chapter we will look at some commonly used functions to manipulate strings.

## strlen() - Return the Length of a String

The PHP strlen() function returns the length of a string.

Return the length of the string "Hello world!":

```
<?php
echo strlen("Hello world!"); // outputs 12
?>
```

## str_word_count() - Count Words in a String

The PHP str_word_count() function counts the 
number of words in a string.

Count the number of word in the string "Hello world!":

```
<?php
echo str_word_count("Hello world!"); // outputs 2
?>
```

## strrev() - Reverse a String

The PHP strrev() function reverses a string.

Reverse the string "Hello world!":

```
<?php
echo strrev("Hello world!"); // outputs !dlrow olleH
?>
```

## strpos() - Search For a Text Within a String

The PHP strpos() function searches for a specific text within a string. If a match is found, the function returns the character position of the first match. If no match is found, it will return FALSE.

Search for the text "world" in the string "Hello world!":


```
<?php
echo strpos("Hello world!", "world"); // outputs 6
?>
```


Tip:  
The first character position in a string is 0 (not 1).


## str_replace() - Replace Text Within a String

The PHP str_replace() function replaces some characters with some other 
characters in a string.

Replace the text "world" with "Dolly":


```
<?php
echo str_replace("world", "Dolly", "Hello world!"); // outputs Hello Dolly!
?>
```

## Complete PHP String Reference

For a complete reference of all string functions, go to our complete PHP String Reference.

[PHP String Reference](php_ref_string.asp)The PHP string reference contains description and example of use, for each function!

## Exercise:


Get the length of the string "Hello World!".