


# PHP MySQL Use The ORDER BY Clause




## Select and Order Data From a MySQL Database


The ORDER BY clause is used to sort the result-set in ascending or descending 
order.


The ORDER BY clause sorts the records in ascending order by default. To sort 
the records in descending order, use the DESC keyword.


```

SELECT column_name(s)
FROM table_name ORDER BY column_name(s) ASC|DESC 
```
To learn more about SQL, please visit our SQL tutorial.

[SQL tutorial](/sql/default.asp)

## Select and Order Data With MySQLi


The following example selects the id, firstname and lastname columns from the MyGuests 
table. The records will be ordered by the lastname column:```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection$conn = new mysqli($servername, $username, $password, $dbname);// Check connectionif ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
 } $sql = "SELECT id, firstname, lastname FROM MyGuests ORDER BY lastname";$result = $conn->query($sql);if ($result->num_rows > 0) {  // output data of each row  while($row = $result->fetch_assoc()) {
      echo "id: " . $row["id"]. " - Name: " . $row["firstname"]. " " . $row["lastname"]. "<br>";
    }} else {  echo "0 results";}
 $conn->close();
?>
```
Code lines to explain from the example above:


First, we set up the SQL query that selects the id, firstname and lastname columns from the MyGuests 
table. The records will be ordered by the lastname column. The next line of code runs the query and puts the resulting data into a 
variable called $result.


Then, the function num_rows() checks if there are more than zero 
rows returned.

If there are more than zero rows returned, the 
function fetch_assoc() puts all the results into an associative array that we can loop 
through. The while() loop loops through the result set and outputs the data from 
the id, firstname and lastname columns.The following example shows the same as the example above, in the MySQLi procedural way:```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);
 // Check connection
 if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());}$sql = "SELECT id, firstname, lastname FROM MyGuests 
  ORDER BY lastname";$result = mysqli_query($conn, $sql);if (mysqli_num_rows($result) > 0) {
    // output data of each row  while($row = mysqli_fetch_assoc($result)) {    echo "id: " . $row["id"]. " - Name: " . $row["firstname"]. " " . $row["lastname"]. "<br>";
    }} else {  echo "0 results";}
mysqli_close($conn);
?>
```


You can also put the result in an HTML table:```
<?php$servername = "localhost";$username = "username";$password = "password";$dbname = "myDB";// Create connection$conn = new mysqli($servername, $username, $password, $dbname);// Check connectionif ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
 } $sql = "SELECT id, firstname, lastname FROM MyGuests ORDER BY lastname";$result = $conn->query($sql);if ($result->num_rows > 0) {  echo "<table><tr><th>ID</th><th>Name</th></tr>";
    // output data of each row  while($row = $result->fetch_assoc()) {    echo "<tr><td>".$row["id"]."</td><td>".$row["firstname"]." ".$row["lastname"]."</td></tr>";
    }  echo "</table>";} else {  echo "0 results";}
 $conn->close();
?>
```

## Select Data With PDO (+ Prepared Statements)


The following example uses prepared statements.


Here we select the id, firstname and lastname columns from the MyGuests table. 
The records will be ordered by the lastname column, and it will be 
displayed in an HTML table:```
<?phpecho "<table style='border: solid 1px black;'>";
 echo "<tr><th>Id</th><th>Firstname</th><th>Lastname</th></tr>";class TableRows extends RecursiveIteratorIterator {
   function __construct($it) {     parent::__construct($it, self::LEAVES_ONLY); 
    }
  function current() {    return "<td style='width:150px;border:1px solid black;'>" . parent::current(). "</td>";
    }  function beginChildren() {     echo "<tr>"; 
    }   function endChildren() {     echo "</tr>" . "\n";
    } } $servername = "localhost";
 $username = "username";$password = "password";$dbname = "myDBPDO";
 try {  $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);  $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $stmt = $conn->prepare("SELECT id, firstname, lastname FROM MyGuests 
  ORDER BY lastname");   $stmt->execute();
  // set the resulting array to associative  $result = $stmt->setFetchMode(PDO::FETCH_ASSOC);   foreach(new TableRows(new RecursiveArrayIterator($stmt->fetchAll())) as $k=>$v) { 
      echo $v;  }} catch(PDOException $e) {  echo "Error: " . $e->getMessage();}$conn = null;echo "</table>";?>
```


