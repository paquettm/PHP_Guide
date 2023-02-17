# Operators

Operators are used to perform operations on variables and values.

PHP divides the operators in the following groups:
* Arithmetic operators
* Assignment operators
* Comparison operators
* Increment/Decrement operators
* Logical operators
* String operators
* Array operators
* Conditional assignment operators

## Arithmetic Operators

The PHP arithmetic operators are used with numeric values to perform common arithmetical operations, such as addition, subtraction, multiplication etc.

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| + | Identity | +$a | Conversion of $a to int or float as appropriate. |
| - | Negation | -$a | Opposite of $a. |
| +	| Addition 	| $a + $b | Sum of $a and $b |	
| -	| Subtraction	$a - $b | Difference of $a and $b |
| *	| Multiplication | $a * $b | Product of $a and $b |
| /	| Division | $a / $b | Quotient of $a and $b |
| %	| Modulus | $a % $b | Remainder of $a divided by $b |
| ** | Exponentiation | $a ** $b | Result of raising $a to the $b'th power |

## Assignment Operators

The PHP assignment operators are used to assign a value to a variable.

The basic assignment operator in PHP is "=". It means that the left operand 
gets set to the value of the assignment expression on the right.

You can assign the value resulting from an operation by writing the mathematical expression to the right of the assignment operator and the variable to the left of the assignment operator, e.g., `$result = $x + $y`

### Arithmetic Assignment Operators
| Example | Equivalent | Operation |
| ------- | ---------- | --------- |
| $a += $b | $a = $a + $b | Addition |
| $a -= $b | $a = $a - $b | Subtraction |
| $a \*= $b | $a = $a * $b | Multiplication |
| $a /= $b | $a = $a / $b | Division |
| $a %= $b | $a = $a % $b | Modulus |
| $a \*\*= $b | $a = $a ** $b | Exponentiation |

### Bitwise Assignment Operators
| Example | Equivalent | Operation |
| ------- | ---------- | --------- |
| $a &= $b | $a = $a & $b | Bitwise And |
| $a |= $b | $a = $a | $b | Bitwise Or |
| $a ^= $b | $a = $a ^ $b | Bitwise Xor |
| $a <<= $b | $a = $a << $b | Left Shift |
| $a >>= $b | $a = $a >> $b | Right Shift |

### Other Assignment Operators
| Example | Equivalent | Operation |
| ------- | ---------- | --------- |
| $a .= $b | $a = $a . $b | String Concatenation |
| $a ??= $b | $a = $a ?? $b | Null Coalesce |

## Comparison Operators

The PHP comparison operators are used to compare two values (number or string):

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| == | Equal | $x == $y | Returns true if $x is equal to $y |
| === | Identical | $x === $y | Returns true if $x is equal to $y, and they are of the same type |
| != | Not equal | $x != $y | Returns true if $x is not equal to $y |
| <> | Not equal | $x <> $y | Returns true if $x is not equal to $y |
| !== | Not identical | $x !== $y | Returns true if $x is not equal to $y, or they are not of the same type |
| > | Greater than | $x > $y | Returns true if $x is greater than $y |
| < | Less than | $x < $y | Returns true if $x is less than $y |
| >= | Greater than or equal to | $x >= $y | Returns true if $x is greater than or equal to $y |
| <= | Less than or equal to | $x <= $y | Returns true if $x is less than or equal to $y |
| <=> | Spaceship | $x <=> $y | Returns an integer less than, equal to, or greater than zero, depending on if $x is less than, equal to, or greater than $y. Introduced in PHP 7. |

## Increment / Decrement Operators

The PHP increment/decrement operators are used to increment/decrement a variable's value (by 1).

| Operator | Name | Description |
| -------- | ---- | ----------- |
| ++$x | Pre-increment | Increments $x by one, then returns $x |
| $x++ | Post-increment | Returns $x, then increments $x by one |
| --$x | Pre-decrement | Decrements $x by one, then returns $x |
| $x-- | Post-decrement | Returns $x, then decrements $x by one |

Increment/decrement operators are a specific case of a broader category of operators called Unary operators: operators that take a single variable as a parameter and act on this single variable. Unary operators that affect the value of the variable can only be used with variables.

## Logical Operators

The PHP logical operators are used to perform arithmetic on Boolean values and therefore combine (Boolean) conditional values statements.

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| and | And | $x and $y | True if both $x and $y are true |
| or | Or | $x or $y | True if either $x or $y is true |
| xor | Xor | $x xor $y | True if either $x or $y is true, but not both |
| && | And | $x && $y | True if both $x and $y are true |
| || | Or | $x || $y | True if either $x or $y is true |
| ! | Not | !$x | True if $x is not true |

## String Operators

PHP has two operators that are specially designed for strings.

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| . | Concatenation | $txt1 . $txt2 | Concatenation of $txt1 and $txt2 |
| .= | Concatenation assignment | $txt1 .= $txt2 | Appends $txt2 to $txt1 |

## PHP Array Operators

The PHP array operators are used to compare arrays.

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| + | Union | $x + $y | Union of $x and $y |
| == | Equality | $x == $y | Returns true if $x and $y have the same key/value pairs |
| === | Identity | $x === $y | Returns true if $x and $y have the same key/value pairs in the same order and of the same types |
| != | Inequality | $x != $y | Returns true if $x is not equal to $y |
| <> | Inequality | $x <> $y | Returns true if $x is not equal to $y |
| !== | Non-identity | $x !== $y | Returns true if $x is not identical to $y |

## PHP Conditional Assignment Operators

The PHP conditional assignment operators are used to set a value depending on conditions:

| Operator | Name | Example | Result |
| -------- | ---- | ------- | ------ |
| ?: | Ternary | $x = expr1 ? expr2 : expr3 | Returns the value of expr2 if expr1 = TRUE or the value of expr3 if expr1 = FALSE |
| ?? | Null coalescing | $x = expr1 ?? expr2 | If expr1 exists, and is not NULL, then returns the value of expr1, else the value of expr2. |

