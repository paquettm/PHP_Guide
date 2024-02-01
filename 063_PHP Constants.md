


# PHP OOP - Class Constants




## PHP - Class Constants


Constants cannot be changed once it is declared.


Class constants can be useful if you need to define some constant data within 
a class.


A class constant is declared inside a class with the const 
keyword.

Class constants are case-sensitive. However, it is recommended to name the constants in 
all uppercase letters.


We can access a constant from outside the class by using the class name 
followed by the scope resolution operator (::) followed by the constant 
name, like here:

```
    <?phpclass 
    Goodbye {  const LEAVING_MESSAGE = "Thank you for visiting cstutoring.ca!";}echo 
    Goodbye::LEAVING_MESSAGE;
    ?>
```
Or, we can access a constant from inside the class by using the 
self keyword followed by the scope resolution operator (::) followed by the constant name, like here:
```
    <?phpclass Goodbye {  const LEAVING_MESSAGE = "Thank you for visiting cstutoring.ca!";  
    public function byebye() {    echo self::LEAVING_MESSAGE;  
    }}$goodbye = new Goodbye();$goodbye->byebye();?>
```