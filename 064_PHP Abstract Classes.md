


# PHP OOP - Abstract Classes




## PHP - What are Abstract Classes and Methods?


Abstract classes and methods are when the parent class has a named method, 
but 
need its child class(es) to fill out the tasks.


An abstract class is a class that contains at least one abstract method. An 
abstract method is a method that is declared, but not implemented in the code.


An abstract class or method is defined with the abstract 
keyword:

```
    <?phpabstract class 
    ParentClass {  abstract public function someMethod1();  
    abstract public function someMethod2($name, $color);  abstract 
    public function someMethod3() : string;}?>
```


When inheriting from an abstract class, the child class method must be 
defined with the same name, and the same or a less restricted access modifier. 
So, if the abstract method is defined as protected, the child class method must 
be defined as either protected or public, but not private. Also, the type and number of 
required arguments must be the same. However, the child classes may have optional 
arguments in addition.


So, when a child class is inherited from an abstract class, we have the following rules:
* The child class method must be defined with the same name and it redeclares the parent abstract method


* The child class method must be defined with the same or a less restricted 
  access modifier


* The number of required arguments must be the same. However, the child class 
  may have optional 
arguments in additionLet's look at an example:```
    <?php// Parent classabstract class Car {  public 
    $name;  public 
    function __construct($name) {    $this->name = $name;  }  
    abstract public function intro() : string;     }// Child classesclass 
    Audi extends Car {  public 
    function intro() : string {    return "Choose German 
    quality! I'm an $this->name!";
      }}class 
    Volvo extends Car {  public 
    function intro() : string {    return "Proud to be 
    Swedish! I'm a $this->name!";
      }}class 
    Citroen extends Car {  public 
    function intro() : string {    return "French 
    extravagance! I'm a $this->name!";
      }}// Create objects from the child classes$audi = new 
    audi("Audi");
    echo $audi->intro();echo "<br>";$volvo = new 
    volvo("Volvo");
    echo $volvo->intro();echo "<br>";
$citroen = new citroen("Citroen");
    echo $citroen->intro();?>
```




The Audi, Volvo, and Citroen classes are inherited from the Car class. This means that the 
Audi, Volvo, and Citroen classes can use the public $name 
property as well as the public \__construct() method from the 
Car class because of inheritance.


But, intro() is an abstract method that should be defined in all the child 
classes and they should return a string.


## PHP - More Abstract Class Examples


Let's look at another example where the abstract method has an argument:```
    <?phpabstract class ParentClass {  // Abstract method 
    with an argument  abstract protected 
    function prefixName($name);}class ChildClass extends ParentClass {  public function prefixName($name) {    
    if ($name == "John Doe") {      $prefix = "Mr.";    
    } elseif ($name == "Jane Doe") {      $prefix = 
    "Mrs.";    } else {      
    $prefix = "";    }    return 
    "{$prefix} {$name}";  }}$class = new ChildClass;echo $class->prefixName("John 
    Doe");echo "<br>"; echo $class->prefixName("Jane Doe");?>
```

Let's look at another example where the abstract method has an argument, and 
the child class has two optional arguments that are not defined in the parent's 
    abstract method:```
    <?phpabstract class ParentClass {  // Abstract method 
    with an argument  abstract protected 
    function prefixName($name);}class ChildClass extends ParentClass {  
    // The child class may define optional arguments that are not in the parent's 
    abstract method  public function prefixName($name, $separator = ".", 
    $greet = "Dear") {    
    if ($name == "John Doe") {      $prefix = "Mr";    
    } elseif ($name == "Jane Doe") {      $prefix = 
    "Mrs";    } else {      
    $prefix = "";    }    return 
    "{$greet} {$prefix}{$separator} {$name}";  }}$class = new ChildClass;echo $class->prefixName("John 
    Doe");echo "<br>"; echo $class->prefixName("Jane Doe");?>
```