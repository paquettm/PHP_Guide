
# PHP Installation and Development Environment

To start using PHP, you can:

* Install an *AMP stack* on your own PC (recommended)
* Install a Web server on your own PC, and then install PHP and MySQL
* Find a Web host with PHP and MySQL support

## Setting up an AMP Stack

The easiest solution to getting up and running quickly with PHP is to install an *AMP stack*, which is a collection of a Web server, a database management system, and the PHP script interpreter. We recommend installing XAMPP which is available from [ApacheFriends.org](https://www.apachefriends.org/).

All you have to do is install the most recent version for the operating system on your PC. There are XAMPP distributions for Linux, Windows and MacOS.

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