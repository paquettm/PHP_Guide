


# PHP OOP - Destructor




## PHP - The \__destruct Function


A destructor is called when the object is destructed or the script is stopped 
or exited.


If you create a \__destruct() function, PHP will automatically call this 
function at the end of the script.

Notice that the destruct function starts with two underscores (\__)!


The example below has a \__construct() function that is automatically called 
when you create an object from a class, and a \__destruct() function that is 
automatically called at the end of the script:```
    <?phpclass Fruit {  public 
    $name;  public $color;  
    function __construct($name) {    $this->name = $name;
      }  
    function __destruct() {    echo "The fruit is {$this->name}.";
      }}$apple = new Fruit("Apple");
    ?>
```

Another example:```
    <?phpclass Fruit {  public 
    $name;  public $color;  
    function __construct($name, $color) {    $this->name = $name;
        $this->color = $color;
      }  
    function __destruct() {    echo "The fruit is {$this->name} 
    and the color is {$this->color}.";
      }}$apple = new Fruit("Apple", "red");
    ?>
```

Tip: As constructors and destructors helps reducing the 
amount of code, they are very useful!
