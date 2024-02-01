


# PHP Example - AJAX Poll




## AJAX Poll


The following example will demonstrate a poll where the result is shown without reloading.

## Example Explained - The HTML Page


When a user chooses an option above, a function called "getVote()" is executed. The 
function is triggered by the "onclick" event:
```
<html>
<head>
<script>
function getVote(int)
{
 
  var xmlhttp=new XMLHttpRequest();
 
xmlhttp.onreadystatechange=function() {
 
  if (this.readyState==4 && this.status==200) {
 
 
  document.getElementById("poll").innerHTML=this.responseText;
    }
  }
 
xmlhttp.open("GET","poll_vote.php?vote="+int,true);
 
xmlhttp.send();
}
</script>
</head>
<body>

<div id="poll">
<h3>Do you like PHP and AJAX so far?</h3>
<form>
Yes:
<input type="radio" name="vote"
value="0" onclick="getVote(this.value)"><br>No:
<input type="radio" name="vote"
value="1" onclick="getVote(this.value)">
</form>
</div>

</body>
</html>

```
The getVote() function does the following:
* Create an XMLHttpRequest object


* Create the function to be executed when the server response is ready


* Send the request off to a file on the server


* Notice that a parameter (vote) is added to the URL (with the value of the yes or no option)## The PHP File


The page on the server called by the JavaScript above is a PHP file called "poll_vote.php":
```
<?php
$vote = $_REQUEST['vote'];

//get content of textfile
$filename = "poll_result.txt";
$content = file($filename);

//put content in array
$array = explode("||", $content[0]);
$yes = $array[0];
$no = $array[1];

if ($vote == 0) {
  $yes = $yes + 1;
 }
if ($vote == 1) {
  $no = $no + 1;
 }

//insert votes to txt file
$insertvote = $yes."||".$no;
$fp = fopen($filename,"w");
fputs($fp,$insertvote);
fclose($fp);
?>

<h2>Result:</h2>
<table>
<tr>
<td>Yes:</td>
<td><img src="poll.gif"
width='<?php echo(100*round($yes/($no+$yes),2)); ?>'
height='20'>
<?php echo(100*round($yes/($no+$yes),2)); ?>%
</td>
</tr>
<tr>
<td>No:</td>
<td><img src="poll.gif"
width='<?php echo(100*round($no/($no+$yes),2)); ?>'
height='20'>
<?php echo(100*round($no/($no+$yes),2)); ?>%
</td>
</tr>
</table>

```
The value is sent from the JavaScript, and the following 
happens:
* Get the content of the "poll_result.txt" file


* Put the content of the file in variables and add one to the selected variable


* Write the result to the "poll_result.txt" file


* Output a graphical representation of the poll result

## The Text File


The text file (poll_result.txt) is where we store the data from the poll. 


It is stored like this:


```
0||0
```The first number represents the "Yes" votes, the second number represents the 
"No" votes.


Note: Remember to allow your web server to edit the text file. Do 
NOT give everyone access, just the web server (PHP).


