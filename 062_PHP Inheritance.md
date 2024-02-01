


# PHP OOP - Inheritance




## PHP - What is Inheritance?


Inheritance in OOP = When a class derives from another class.


The child class will inherit all the public and protected properties and 
methods from the parent class. In addition, it can have its own properties and 
methods.


An inherited class is defined by using the extends 
keyword.

Let's look at an example:```
    <?phpclass Fruit {  public 
    $name;  public $color;  public 
    function __construct($name, $color) {    $this->name = $name;    $this->color = $color;
      }  
    public function intro() {    echo "The fruit is {$this->name} 
    and the color is {$this->color}.";
      }}// Strawberry is inherited from Fruitclass 
    Strawberry extends Fruit {  public 
    function message() {    echo "Am I a fruit or a 
    berry? ";
      }}$strawberry = new Strawberry("Strawberry", "red");$strawberry->message();$strawberry->intro();
    ?>
```



The Strawberry class is inherited from the Fruit class. 


This means that the Strawberry class can use the public $name and $color 
properties as well as the public \__construct() and intro() methods from the 
Fruit class because of inheritance.


The Strawberry class also has its own method: message().


## PHP - Inheritance and the Protected Access Modifier


In the previous chapter we learned that protected properties or methods can 
  be accessed within the 
  class and by classes derived from that class. What does that mean?

Let's look at an example:```
    <?phpclass Fruit {  public 
    $name;  public $color;  public 
    function __construct($name, $color) {    $this->name = $name;    $this->color = $color;
      }  
    protected function intro() {    echo "The fruit is {$this->name} 
    and the color is {$this->color}.";
      }}class 
    Strawberry extends Fruit {  public 
    function message() {    echo "Am I a fruit or a 
    berry? ";
      }}// Try to call all three methods from outside class$strawberry = new Strawberry("Strawberry", "red");  
    // OK. __construct() is public$strawberry->message(); // OK. message() 
    is public$strawberry->intro(); // ERROR. intro() 
    is protected
    ?>
```

In the example above we see that if we try to call a protected 
method (intro()) from outside the class, we will receive an error. public 
methods will work fine!Let's look at another example:```
    <?phpclass Fruit {  public $name;  public 
    $color;  public function __construct($name, $color) {    
    $this->name = $name;    $this->color = $color;   
    }  protected function intro() {    echo "The 
    fruit is {$this->name} and the color is {$this->color}.";   }}
class Strawberry extends Fruit {  public function message() {    
    echo "Am I a fruit or a berry? ";    // Call protected 
    method from within derived class - OK    $this -> 
    intro();  }}
    $strawberry = new Strawberry("Strawberry", "red"); // OK. __construct() is 
    public$strawberry->message(); // OK. message() is 
    public and it calls intro() (which is protected) from within the 
    derived class?>
```


In the example above we see that all works fine! It is because we call the
protected 
method (intro()) from inside the derived class.## PHP - Overriding Inherited Methods


Inherited methods can be overridden by redefining the methods (use the same 
name) in the child class.


Look at the example below. The \__construct() and intro() methods in the child 
class (Strawberry) will override the \__construct() and intro() methods in the 
parent class (Fruit):```
    <?phpclass Fruit {  public 
    $name;  public $color;  public 
    function \__construct($name, $color) {    $this->name = $name;    $this->color = $color;
      }  
    public function intro() {    echo "The fruit is {$this->name} 
    and the color is {$this->color}.";
      }}class 
    Strawberry extends Fruit {  public $weight;  public 
    function \__construct($name, $color, $weight) {    $this->name = $name;    $this->color = $color;    $this->weight = $weight;
      }  
    public function intro() {    echo "The fruit is {$this->name}, the color is {$this->color}, 
    and the weight is {$this->weight} gram.";
      }}$strawberry = new Strawberry("Strawberry", "red", 
    50);$strawberry->intro();?>
```

## PHP - The final Keyword


The final 
keyword can be used to prevent class inheritance or to prevent method overriding.

The following example shows how to prevent class inheritance:```
    <?phpfinal class Fruit {  // some code }// 
    will result in errorclass 
    Strawberry extends Fruit {  // some code}?>
```

The following example shows how to prevent method overriding:```
    <?phpclass Fruit {  
    final public function intro() {    // some code  }}class 
    Strawberry extends Fruit {  // 
    will result in error  
    public function intro() {    // some code  }}?>
```
