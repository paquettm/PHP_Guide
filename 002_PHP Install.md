
# PHP Installation and Development Environment

To start using PHP, you can:

* Install an *AMP stack* on your own PC (recommended)
* Install a Web server on your own PC, and then install PHP and MySQL
* Find a Web host with PHP and MySQL support

## Setting up an AMP Stack

### XAMPP

The easiest solution to getting up and running quickly with PHP is to install an *AMP stack*, which is a collection of a Web server, a database management system, and the PHP script interpreter. We recommend installing XAMPP which is available from [ApacheFriends.org](https://www.apachefriends.org/).

All you have to do is install the most recent version for the operating system on your PC. There are XAMPP distributions for Linux, Windows and MacOS.

### Docker 
GitHub user [tomsik68](https://github.com/tomsik68) has set up a [Dockerfile producing a docker image to contain XAMPP](https://github.com/tomsik68/docker-xampp). The image can be deployed without compilation with the simple commands (for Windows)
```
docker run --name myXampp -p 22:22 -p 80:80 -d -v C:/path/to/local/web/root:/opt/lampp/htdocs tomsik68/xampp
```
where `C:/path/to/local/web/root` is the location on your computer where you are placing your Web application code. This location will be mounted to the container and accessed by its contained servers.
You can simply create/edit your Web application locally directly in your `C:/path/to/local/web/root` folder.

**(Not completely tested)** You may save the docker image on USB for "ease of transportation" and to avoid having to download again using.

Commit any changes you need to keep.
```
docker commit myXampp tomsik68/xampp 
```
Save the image to an archive on your USB device.
```
docker save tomsik68/xampp -o d:/myXampp.tar 
```
Load the image to use again with the above docker run command.
```
docker load -i d:\myXampp.tar
```

## Set Up PHP on Your Own PC

However, if your server does not support PHP, you can:

* install a Web server
* install PHP
* install a database, such as MySQL

The official PHP website (PHP.net) has installation instructions for PHP: [http://php.net/manual/en/install.php](http://php.net/manual/en/install.php)

## Use a Web Host With PHP Support
If your server has activated support for PHP you do not 
need to do anything.

Just create some .php files, place them in your web directory, and the server 
will automatically parse them for you.

You do not need to compile anything or install any extra tools.

Because PHP is free, most web hosts offer PHP support.

## Development Environment

Now that you have a server that runs PHP, you need software to edit text files and keep your project organized.

You may use any code editor that you want such as VS Code. Make sure that you understand the relation of where files are placed in your code editor arborescence vs where the files are placed in your computer file system.

An easily installed coding solution for PHP is [Sublime Text](https://www.sublimetext.com/download). At the time of writing this guide, Sublime Text is at its version 4.

### Knowing your Document Root

You must place your PHP code in your server document root. By default, for a XAMPP installation, this will be in the xampp\htdocs folder.

If however this is not the case for your installation of Apache, you can check in your apache configuration files under apache's folder, look for the conf\httpd.conf file and look for the path next to the `DocumentRoot` keyword.
