


# PHP Connect to MySQL




PHP 5 and later can work with a MySQL database using:
* MySQLi extension (the "i" stands for improved)
* PDO (PHP Data Objects)
Earlier versions of PHP used the MySQL extension. However, this 
extension was deprecated in 2012.
## Should I Use MySQLi or PDO?


If you need a short answer, it would be "Whatever you like".


Both MySQLi and PDO have their advantages:


PDO will work on 12 different database systems, whereas MySQLi will only 
work with MySQL databases.


So, if you have to switch your project 
to use another database, PDO makes the process easy. You only have 
to change the connection string and a few queries. With MySQLi, you will need 
to rewrite the entire code - queries included.


Both are object-oriented, but MySQLi also offers a procedural API.


Both support Prepared Statements. Prepared Statements protect 
from SQL injection, and are very important for web application security.
## MySQL Examples in Both MySQLi and PDO Syntax


In this, and in the following chapters we demonstrate three ways of working 
with PHP and MySQL:
* MySQLi (object-oriented)


* MySQLi (procedural)


* PDO

## MySQLi Installation


For Linux and Windows: The MySQLi extension is automatically installed in 
most cases, when php5 mysql package is installed.


For installation details, go to:

http://php.net/manual/en/mysqli.installation.php

[
http://php.net/manual/en/mysqli.installation.php](http://php.net/manual/en/mysqli.installation.php)
## PDO Installation


For installation details, go to:

http://php.net/manual/en/pdo.installation.php

[
http://php.net/manual/en/pdo.installation.php](http://php.net/manual/en/pdo.installation.php)


## Open a Connection to MySQL


Before we can access data in the MySQL database, we need to be able to connect to 
the server:```
<?php$servername = "localhost";$username = "username";$password = "password";// Create connection$conn = new mysqli($servername, $username, $password);
// Check connection
 if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);}
echo "Connected successfully";
?>
```

Note on the object-oriented example above: 
$connect_error was 
broken until PHP 5.2.9 and 5.3.0. If you need to ensure compatibility with PHP 
versions prior to 5.2.9 and 5.3.0, use the following code instead:
// Check connectionif (mysqli_connect_error()) {  die("Database connection failed: " . mysqli_connect_error());}```
<?php$servername = "localhost";$username = "username";
 $password = "password";// Create connection
$conn = mysqli_connect($servername, $username, $password);
// Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}echo "Connected successfully";
?>
``````
<?php$servername = "localhost";$username = "username";
 $password = "password";try {  $conn = new PDO("mysql:host=$servername;dbname=myDB", $username, $password);
    // set the PDO error mode to exception  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Connected successfully";
 } catch(PDOException $e) {  echo "Connection failed: " . $e->getMessage();}
?>
```

Note: In the PDO example above we have also 
specified a database (myDB). PDO require a valid database 
to connect to. If no database is specified, an exception is thrown.Tip: A great benefit of PDO is that it 
has an exception class to handle any problems that may 
occur in our database queries. If an exception is thrown within the try{ } block, 
the script stops executing and flows directly to the first catch(){ } block.


## Close the Connection


The connection will be closed automatically when the script ends. To close the 
connection before, use the following:```
$conn->close();```

```
mysqli_close($conn);
```

```
$conn = null;
```
