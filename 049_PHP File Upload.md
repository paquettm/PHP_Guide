


# PHP File Upload




With PHP, it is easy to upload files to the server.


However, with ease comes danger, so always be careful when 
allowing file uploads!
## Configure The "php.ini" File


First, ensure that PHP is configured to allow file uploads.


In your "php.ini" file, search for the file_uploads directive, and set it to On:```
file_uploads = On
```

## Create The HTML Form


Next, create an HTML form that allow users to choose the image file they want to upload:
```
 <!DOCTYPE html><html><body><form action="upload.php" method="post"
enctype="multipart/form-data">  Select image to upload:  <input type="file" name="fileToUpload" id="fileToUpload">
    <input type="submit" value="Upload Image" name="submit">
</form></body></html>
```

Some rules to follow for the HTML form above:
* Make sure that the form uses method="post"


* The form also needs the following attribute: enctype="multipart/form-data". It specifies which content-type to use when submitting the formWithout the requirements above, the file upload will not work.


Other things to notice:
* The type="file" attribute of the <input> tag shows the input field as a file-select control, with a "Browse" button next to the input control The form above sends data to a file called "upload.php", which we will create next.


## Create The Upload File PHP Script


The "upload.php" file contains the code for uploading a file:
```
<?php$target_dir = "uploads/";$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);$uploadOk = 1;$imageFileType = 
  strtolower(pathinfo($target_file,PATHINFO_EXTENSION));// Check if image file is a actual image or fake imageif(isset($_POST["submit"])) {
    $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);  if($check !== false) {    echo "File is an image - " . $check["mime"] . ".";    $uploadOk = 1;
    } else {    echo "File is not an image.";
      $uploadOk = 0;  }}?>
```PHP script explained:
* $target_dir = "uploads/" - specifies the directory where the file is going to be placed


* $target_file specifies the path of the file to be uploaded


* $uploadOk=1 is not used yet (will be used later)


* $imageFileType holds the file extension of the file (in lower case)


* Next, check if the image file is an actual image or a fake image

Note: You will need to create a new directory called 
"uploads" in the 
directory where "upload.php" file resides. The uploaded files 
will be saved there.


Note: You will need to create a new directory called 
"uploads" in the 
directory where "upload.php" file resides. The uploaded files 
will be saved there.## Check if File Already Exists


Now we can add some restrictions.


First, we will check if the file already exists in the "uploads" folder. If 
it does, an error message is displayed, and $uploadOk is set to 0:
```
// Check if file already existsif (file_exists($target_file)) {  echo "Sorry, file already exists.";
    $uploadOk = 0;
 } ```
## Limit File Size


The file input field in our HTML form above is named "fileToUpload".


Now, we want to check the size of the file. If the file is larger than 500KB, an error message is displayed, and $uploadOk is set to 0:
```
// Check file sizeif ($_FILES["fileToUpload"]["size"] > 500000) {
    echo "Sorry, your file is too large.";  $uploadOk = 0;
 } ```
## Limit File Type


The code below only allows users to upload JPG, JPEG, PNG, and GIF files. All other 
file types gives an error message before setting $uploadOk to 0:
```
// Allow certain file formatsif($imageFileType != "jpg" && $imageFileType  != "png" && $imageFileType != "jpeg"&& $imageFileType != "gif" ) {  echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";  $uploadOk = 0;}
```


## Complete Upload File PHP Script


The complete "upload.php" file now looks like this:
```
<?php$target_dir = "uploads/";$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);$uploadOk = 1;$imageFileType = 
  strtolower(pathinfo($target_file,PATHINFO_EXTENSION));// Check if image file is a actual image or fake imageif(isset($_POST["submit"])) {  $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);  if($check !== false) {    echo "File is an image - " . $check["mime"] . ".";
      $uploadOk = 1;  } else {    echo "File is not an image.";
      $uploadOk = 0;  }}// Check if file already existsif (file_exists($target_file)) {
    echo "Sorry, file already exists.";  $uploadOk = 0;}
 // Check file sizeif ($_FILES["fileToUpload"]["size"] > 500000) {  echo "Sorry, your file is too large.";  $uploadOk = 0;
 }// Allow certain file formatsif($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg"&& $imageFileType != "gif" ) {  echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";  $uploadOk = 0;}// Check if $uploadOk is set to 0 by an errorif ($uploadOk == 0) {  echo "Sorry, your file was not uploaded.";// if everything is ok, try to upload file} else {
    if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target_file)) {
      echo "The file ". htmlspecialchars( basename( $_FILES["fileToUpload"]["name"])). 
  " has been uploaded.";
    } else {    echo "Sorry, there was an error uploading your file.";
    }}?>
```


## Complete PHP Filesystem Reference


For a complete reference of filesystem functions, go to our complete
PHP Filesystem Reference.

[PHP Filesystem Reference](php_ref_filesystem.asp)