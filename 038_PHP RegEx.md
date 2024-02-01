


# PHP Regular Expressions




## What is a Regular Expression?


A regular expression is a sequence of characters that forms a search pattern.
When you search for data in a text, you can use this search pattern to describe what you
are searching for.


A regular expression can be a single character, or a more complicated pattern.


Regular expressions can be used to perform all types of text search and text replace
operations.
## Syntax


In PHP, regular expressions are strings composed of delimiters, a pattern and optional
modifiers.


```
$exp = "/cstutoring/i";
```
In the example above, / is the delimiter, "cstutoring" is the pattern that is being searched for,
and i is a modifier that makes the search case-insensitive.


The delimiter can be any character that is not a letter, number, backslash or space. The
most common delimiter is the forward slash (/), but when your pattern contains forward
slashes it is convenient to choose other delimiters such as # or ~.
## Regular Expression Functions


PHP provides a variety of functions that allow you to use regular expressions. The
preg_match(), preg_match_all() and preg_replace() functions are some of the
most commonly used ones:## Using preg_match()


The preg_match() function will tell you whether a string contains matches of a pattern.

Use a regular expression to do a case-insensitive search for "cstutoring" in a string:


```
 <?php$str = "Visit cstutoring.ca";$pattern = "/cstutoring/i";echo 
  preg_match($pattern, $str); // Outputs 1?>```



## Using preg_match_all()


The preg_match_all() function will tell you how many matches were found for a pattern in a
string.

Use a regular expression to do a case-insensitive count of the number of
occurrences of "ain" in a string:


```
 <?php$str = "The rain in SPAIN falls mainly on the plains.";
  $pattern = "/ain/i";echo preg_match_all($pattern, $str); // Outputs 4?>```



## Using preg_replace()


The preg_replace() function will replace all of the matches of the pattern in a string with
another string.

Use a case-insensitive regular expression to replace Microsoft with
cstutoring.ca in a string:


```
 <?php$str = "Visit Microsoft!";$pattern = "/microsoft/i";echo 
  preg_replace($pattern, "cstutoring.ca", $str); // Outputs "Visit
  cstutoring.ca!"?>```

## Regular Expression Modifiers


Modifiers can change how a search is performed.## Regular Expression Patterns


Brackets are used to find a range of characters:

## Metacharacters


Metacharacters are characters with a special meaning:

## Quantifiers


Quantifiers define quantities:Note: If your expression needs to search for one of the special characters you can use a
backslash ( \ ) to escape them.
For example, to search for one or more question marks you can use the following
expression: $pattern = '/\?+/';## Grouping


You can use parentheses ( ) to apply quantifiers to entire patterns. They also can be used
to select parts of the pattern to be used as a match.

Use grouping to search for the word "banana" by looking for ba followed by
two instances of na:```
 <?php$str = "Apples and bananas.";$pattern = "/ba(na){2}/i";echo 
  preg_match($pattern, $str); // Outputs 1?>```



## Complete RegExp Reference


For a complete reference, go to our Complete PHP Regular Expression Reference.

[Complete PHP Regular Expression Reference](php_ref_regex.asp)The reference contains descriptions and examples of all Regular Expression functions.