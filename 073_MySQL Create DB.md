


# PHP Create a MySQL Database




A database consists of one or more tables. 


You will need special CREATE privileges to create or to delete a MySQL 
database.
## Create a MySQL Database Using MySQLi and PDO


The CREATE DATABASE statement is used to create a database in MySQL.


The following examples create a database named "myDB":```
<?php$servername = "localhost";$username = "username";$password = "password";// Create connection$conn = new mysqli($servername, $username, $password);
 // Check connection
 if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);}

// Create database
 $sql = "CREATE DATABASE myDB";if ($conn->query($sql) === TRUE) {  echo "Database created successfully";} else {  echo "Error creating database: " . $conn->error;}$conn->close();
?>
```


Note: When you create a new database, you must only specify 
the first three arguments to the mysqli object (servername, username and 
password).Tip: If you have to use a specific port,
add an empty string for the database-name argument, like this: new mysqli("localhost", 
"username", "password", "", port)

```
<?php$servername = "localhost";$username = "username";$password = "password";// Create connection
$conn = mysqli_connect($servername, $username, $password);
 // Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}// Create database
 $sql = "CREATE DATABASE myDB";
 if (mysqli_query($conn, $sql)) {  echo "Database created successfully";} else {  echo "Error creating database: " . mysqli_error($conn);}mysqli_close($conn);
?>
```Note: The following PDO example create a database named "myDBPDO":
```
<?php$servername = "localhost";$username = "username";
 $password = "password";try {  $conn = new PDO("mysql:host=$servername", $username, $password);
    // set the PDO error mode to exception  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $sql = "CREATE DATABASE myDBPDO";  // use exec() because no results are returned
    $conn->exec($sql);  echo "Database created successfully<br>";} catch(PDOException $e) 
  {  echo $sql . "<br>" . $e->getMessage();
  }
$conn = null;
?>
```
Tip: A great benefit of PDO is that it has exception class to handle any problems that may 
occur in our database queries. If an exception is thrown within the try{ } block, 
the script stops executing and flows directly to the first catch(){ } block. In the catch block above we echo the SQL statement and 
the generated error message. 