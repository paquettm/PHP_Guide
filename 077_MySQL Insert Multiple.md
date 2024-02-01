


# PHP MySQL Insert Multiple Records




## Insert Multiple Records Into MySQL Using MySQLi and PDO


Multiple SQL statements must be executed with the mysqli_multi_query() function.

The following examples add three new records to the "MyGuests" table:```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection$conn = new mysqli($servername, $username, $password, $dbname);
 // Check connection
 if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);}

$sql = "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('John', 'Doe', 'john@example.com');";
 $sql .= "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('Mary', 'Moe', 'mary@example.com');";
 $sql .= "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('Julie', 'Dooley', 'julie@example.com')";
if ($conn->multi_query($sql) === TRUE) {  echo "New records created successfully";} else {  echo "Error: " . $sql . "<br>" . $conn->error;}$conn->close();
?>
```

Note that each SQL statement must be separated by a semicolon.```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);
 // Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}$sql = "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('John', 'Doe', 'john@example.com');";
 $sql .= "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('Mary', 'Moe', 'mary@example.com');";
 $sql .= "INSERT INTO MyGuests (firstname, lastname, email)
 VALUES ('Julie', 'Dooley', 'julie@example.com')";
if (mysqli_multi_query($conn, $sql)) {  echo "New records created successfully";} else {  echo "Error: " . $sql . "<br>" . mysqli_error($conn);}mysqli_close($conn);
?>
```


The PDO way is a little bit different:```
<?php$servername = "localhost";$username = "username";
 $password = "password";$dbname = "myDBPDO";try {
    $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
    // set the PDO error mode to exception  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    // begin the transaction  $conn->beginTransaction();  // our SQL statements
    $conn->exec("INSERT INTO MyGuests (firstname, lastname, email)   VALUES ('John', 'Doe', 'john@example.com')");
    $conn->exec("INSERT INTO MyGuests (firstname, lastname, email)   VALUES ('Mary', 'Moe', 'mary@example.com')");
    $conn->exec("INSERT INTO MyGuests (firstname, lastname, email)   VALUES ('Julie', 'Dooley', 'julie@example.com')");  // commit the transaction  $conn->commit();  echo "New records created successfully";
  } catch(PDOException $e) {  // roll back the transaction if something failed  $conn->rollback();
    echo "Error: " . $e->getMessage();}
$conn = null;
?>
```

