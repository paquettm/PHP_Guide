


# PHP MySQL Get Last Inserted ID




## Get ID of The Last Inserted Record


If we perform an INSERT or UPDATE on a table with an AUTO_INCREMENT field, we can 
get the ID of the last inserted/updated record immediately.


In the table "MyGuests", the "id" column is an AUTO_INCREMENT 
field:
```
CREATE TABLE MyGuests (
id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
firstname VARCHAR(30) NOT NULL,
lastname VARCHAR(30) NOT NULL,
email VARCHAR(50),
reg_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
)
```


The following examples are equal to the examples from the previous page (PHP Insert Data Into 
MySQL), except that we have added one single line of code to retrieve the ID 
of the last inserted record. We also echo the last inserted ID:

[PHP Insert Data Into 
MySQL](php_mysql_insert.asp)```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection$conn = new mysqli($servername, $username, $password, $dbname);
 // Check connection
 if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);}

$sql = "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('John', 'Doe', 'john@example.com')";
if ($conn->query($sql) === TRUE) {  $last_id = $conn->insert_id;
    echo "New record created successfully. Last inserted ID is: " . $last_id;} else {
    echo "Error: " . $sql . "<br>" . $conn->error;}$conn->close();
?>
```


```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);
 // Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}$sql = "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('John', 'Doe', 'john@example.com')";
if (mysqli_query($conn, $sql)) {  $last_id = mysqli_insert_id($conn);  echo "New record created successfully. Last inserted ID is: " . $last_id;} else {  echo "Error: " . $sql . "<br>" . mysqli_error($conn);}mysqli_close($conn);
?>
```

```
<?php$servername = "localhost";$username = "username";
 $password = "password";$dbname = "myDBPDO";try {  $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);  // set the PDO error mode to exception  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $sql = "INSERT INTO MyGuests (firstname, lastname, email)
   
 VALUES ('John', 'Doe', 'john@example.com')";
    // use exec() because no results are returned  $conn->exec($sql);  $last_id = $conn->lastInsertId();  echo "New record created successfully. Last inserted ID is: " . $last_id;} catch(PDOException $e) {  echo $sql . "<br>" . $e->getMessage();
  }
$conn = null;
?>
```

