


# PHP OOP - Static Properties




## PHP - Static Properties


Static properties can be called directly - without creating an instance of a 
class.


Static properties are declared with the static 
keyword:

```
<?php
class ClassName {
    public static $staticProp = "cstutoring.ca";
}
?>
```


To access a static property use the class name, double colon (::), and the 
property name:
```
ClassName::$staticProp;
```
Let's look at an example:
```
<?phpclass 
pi {
    public static $value = 3.14159;
}
// Get static property
echo pi::$value;
?>
```


Here, we declare a static property: $value. Then, we echo the value of the static 
property 
by using the class name, double colon (::), and the property name (without creating a class 
first).


## PHP - More on Static Properties


A class can have both static and non-static properties. A static property can be 
accessed from a method in the same class using the self 
keyword and double colon (::):

```
<?php
class pi {
    public static $value=3.14159;

    public function staticValue() {
        return self::$value;
    }
}
$pi = new pi();
echo $pi->staticValue();
?>
```
To call a static property from a child class, use the parent 
keyword inside the child class:

```
<?php
class pi {
    public static $value=3.14159;
}
class x extends pi {
    public function xStatic() {
        return parent::$value;
    }
}
// Get value of static property directly via child class
echo x::$value;
// or get value of static property via xStatic() method
$x = new x();
echo $x->xStatic();
?>
```