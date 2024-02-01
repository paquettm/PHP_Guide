


# PHP Namespaces




## PHP Namespaces


Namespaces are qualifiers that solve two different problems:
* They allow for better organization by grouping classes that work together to perform
a task


* They allow the same name to be used for more than one classFor example, you may have a set of classes which describe an HTML table, such as Table, Row and
Cell while also having another set of classes to describe furniture, such as Table,
Chair and Bed. Namespaces can be used to organize the classes into two different
groups while also preventing the two classes Table and Table from being mixed up.
## Declaring a Namespace


Namespaces are declared at the beginning of a file using the namespace keyword:

Declare a namespace called Html:


```
    <?phpnamespace Html;?>
  ```
Note: A namespace declaration must be the first thing in the PHP file. The following code
would be invalid:
```
    <?phpecho "Hello World!";namespace Html;...?>```Constants, classes and functions declared in this file will belong to the Html namespace:

Create a Table class in the Html namespace:


```
    <?phpnamespace Html;class Table {  public $title = "";  public 
    $numRows = 0;  public function message() {    echo "<p>Table 
    '{$this->title}' has {$this->numRows} rows.</p>";  }}$table = new 
    Table();$table->title = "My table";$table->numRows = 5;?>
<!DOCTYPE html>
    <html><body><?php $table->message(); ?></body></html>```

For further organization, it is possible to have nested namespaces:Declare a namespace called Html inside a namespace called Code:


```
    <?phpnamespace Code\Html;?>
  ```


## Using Namespaces


Any code that follows a namespace declaration is operating inside the namespace, so
classes that belong to the namespace can be instantiated without any qualifiers. To access
classes from outside a namespace, the class needs to have the namespace attached
to it.

Use classes from the Html namespace:


```
    <?php$table = new Html\Table()$row = new Html\Row();?>```When many classes from the same namespace are being used at the same time, it is
easier to use the namespace keyword:

Use classes from the Html namespace without the need for the Html\qualifier:


```
    <?phpnamespace Html;$table = new Table();$row = new Row();?>```



## Namespace Alias


It can be useful to give a namespace or class an alias to make it easier to write. This is
done with the use keyword:

Give a namespace an alias:


```
    <?phpuse Html as H;$table = new H\Table();?>```Give a class an alias:


```
    <?phpuse Html\Table as 
    T;$table = new T();?>```