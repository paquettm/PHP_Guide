


# PHP - AJAX and MySQL




AJAX can be used for interactive communication with a database.
## AJAX Database Example


The following example will demonstrate how a web page can fetch information from a database with AJAX:
## Example Explained - The MySQL Database


The database table we use in the example above looks like this:


## Example Explained


In the example above, when a user selects a person in the dropdown list 
above, a function called "showUser()" is executed.


The function is triggered by the onchange event.


Here is the HTML code:```
 <html><head><script>function showUser(str) {  if (str == "") {
      document.getElementById("txtHint").innerHTML = "";    return;
    } else {     var xmlhttp = new XMLHttpRequest();    xmlhttp.onreadystatechange = function() {      if (this.readyState == 4 && this.status == 200) {        document.getElementById("txtHint").innerHTML = this.responseText;
        }    };    xmlhttp.open("GET","getuser.php?q="+str,true);
      xmlhttp.send();  }}</script></head><body><form>
 <select name="users" onchange="showUser(this.value)">  <option value="">Select a person:</option>  <option value="1">Peter Griffin</option>  <option value="2">Lois Griffin</option>  <option value="3">Joseph Swanson</option>  <option value="4">Glenn Quagmire</option>  </select></form><br><div id="txtHint"><b>Person info will be listed here...</b></div></body></html>```Code explanation:


First, check if person is selected. If no person is selected (str == ""), clear the 
content of txtHint and exit the function. If a person is selected, do the following:
* Create an XMLHttpRequest object


* Create the function to be executed when the server response is ready


* Send the request off to a file on the server


* Notice that a parameter (q) is added to the URL (with the content of the dropdown list)## The PHP File


The page on the server called by the JavaScript above is a PHP file called "getuser.php".


The source code in "getuser.php" runs a query against a MySQL database, and returns the result in an HTML 
table:
```
 <!DOCTYPE html><html><head><style>table {  width: 100%;  border-collapse: collapse;}
 table, td, th {  border: 1px solid black;  padding: 5px;}th {text-align: left;}</style></head>
 <body><?php$q = intval($_GET['q']);

$con = mysqli_connect('localhost','peter','abc123');
if (!$con) {
  die('Could not connect: ' . mysqli_error($con));
 }

mysqli_select_db($con,"ajax_demo");
$sql="SELECT * FROM user WHERE id = '".$q."'";
$result = mysqli_query($con,$sql);

echo "<table>
<tr>
<th>Firstname</th>
<th>Lastname</th>
<th>Age</th>
<th>Hometown</th>
<th>Job</th>
</tr>";
while($row = mysqli_fetch_array($result)) {
    echo "<tr>";
  echo "<td>" . $row['FirstName'] . "</td>";
    echo "<td>" . $row['LastName'] . "</td>";
  echo "<td>" . $row['Age'] . "</td>";
    echo "<td>" . $row['Hometown'] . "</td>";
  echo "<td>" . $row['Job'] . "</td>";
    echo "</tr>";
 }
echo "</table>";
mysqli_close($con);
?></body></html>```
Explanation: When the query is sent from the JavaScript to the PHP file, the following happens:
* PHP opens a connection to a MySQL server


* The correct person is found


* An HTML table is created, filled with data, and sent back to the "txtHint" placeholder