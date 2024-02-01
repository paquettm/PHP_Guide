


# PHP MySQL Update Data




## Update Data In a MySQL Table Using MySQLi and PDO


The UPDATE statement is used to update existing records in a table:


```
UPDATE table_name
SET column1=value, column2=value2,...
WHERE some_column=some_value 
```
Notice the WHERE clause in the UPDATE syntax: The WHERE clause 
specifies which record or records that should be updated. If you omit the WHERE 
clause, all records will be updated!

To learn more about SQL, please visit our SQL tutorial.

[SQL tutorial](/sql/default.asp)Let's look at the "MyGuests" table:The following examples update the record with id=2 in the "MyGuests" table:```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection$conn = new mysqli($servername, $username, $password, $dbname);
 // Check connection
 if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);}

$sql = "UPDATE MyGuests SET lastname='Doe' WHERE id=2";
if ($conn->query($sql) === TRUE) {  echo "Record updated successfully";} else {  echo "Error updating record: " . $conn->error;}$conn->close();
?>
```


```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);
 // Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}$sql = "UPDATE MyGuests SET lastname='Doe' WHERE id=2";
if (mysqli_query($conn, $sql)) {  echo "Record updated successfully";} else {
    echo "Error updating record: " . mysqli_error($conn);}mysqli_close($conn);
?>
```


```
<?php$servername = "localhost";$username = "username";
 $password = "password";$dbname = "myDBPDO";try {
    $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
    // set the PDO error mode to exception  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
   
 $sql = "UPDATE MyGuests SET lastname='Doe' WHERE id=2";
  // Prepare statement  $stmt = $conn->prepare($sql);  // execute the query
    $stmt->execute();  // echo a message to say the UPDATE succeeded
    echo $stmt->rowCount() . " records UPDATED successfully";} catch(PDOException $e) 
  {  echo $sql . "<br>" . $e->getMessage();}
$conn = null;
?>
```After the record is updated, the table will look like this: