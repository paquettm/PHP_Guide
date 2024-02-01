# Bootstrapping Web Applications with .htaccess

The `.htaccess` file allows us to perform several security and modification operations for our Web applications to work as intended.

Let's consider the example .htaccess file as follows:

```
Options -Indexes
Options -MultiViews
RewriteEngine On
RewriteBase /
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.+)$ index.php?url=$1 [QSA,L]
RewriteRule ^()$ index.php?url=$1 [QSA,L]
```

## Options

Options are set mainly to change folder access. We set these options on or off respectively with + and -.

**Indexes**

When allowed, Indexes allows the listing of all files in a folder by accessing this through a request. Therefore, is is especially important to turn this option off (with -) to not reveal the contents of your folders. This will make it harder to exploit your system for evil intents.

**MultiViews**

When turned on, MultiViews may cause substitute files to be read when others are required that incompletely match the name of those present on the server. In the case of an MVC application, we wish to completely route the application based on requests not matching the files in the system, and furthermore, we wish to still allow resources to be directly loaded by the browser. We must turn off this option.

## URL Rewriting

One useful thing Apache can do to make your MVC Web application work well if to rewrite URLs in such a way that the URL becomes a parameter for a PHP application entry point.

**RewriteEngine On**

Before any URL rewriting happens, we must turn on the rewriting engine.

**RewriteBase**

The RewriteBase directive specifies the URL prefix to be used for per-directory (htaccess) RewriteRule directives that substitute a relative path. Here, we wish to call the index.php file in the Web server document root.

**RewriteCond directive**

The RewriteCond directive defines a rule condition. One or more RewriteCond can precede a RewriteRule directive. The following RewriteRule is then only used if the current state of the URI matches its pattern, and if all these conditions are met.

REQUEST_FILENAME is the full local filesystem path to the file or script matching the request. 

-f: Is regular file. (alternatively !-f is NOT regular file.)
Treats the TestString as a pathname and tests whether or not it exists, and is a regular file.

-d: Is directory. (alternatively !-d is NOT directory.)
Treats the TestString as a pathname and tests whether or not it exists, and is a directory.

```
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !-f
```

So the above sets conditions that the requested file is neither a file or folder that exists. This will allow the browser to fetch stylesheets, libraries, etc. from the resources without having to be routed by the MVC application.

**RewriteRule**

This sets the rule that will be run once the conditions are met. In the above example

```
RewriteRule ^(.+)$ index.php?url=$1 [QSA,L]
RewriteRule ^()$ index.php?url=$1 [QSA,L]
```

the first rule matches any url segment following the server address of non-zero length from the incoming requested URL. The second rule matches requests where that segment has a zero length. This URL segment is sent to index.php, through the `url` query string parameter.

Any other query string parameters are added by virtue of the QSA (Query String Append) flag. The L flag ensures that no further rules are applied to this request if this rule is run.

**RewriteRule flags**

For more information on applicable RewriteRule flags, consult the documentation at https://httpd.apache.org/docs/2.4/rewrite/flags.html.

## Taking security one step further

One more .htaccess file is needed in private downstream folders such that files from these are never accessible trough direct HTTP requests. The file is as follows:

```
Options -Indexes
Deny from all
```

This will not allow users to list contents of any folder as well as disallow direct access to any file through external requests. Only your internal code will be able to include, require and run this code.

## Completing the application

Consider the above .htaccess file is in the Apache server document root with the following index.php file:

```
<?php
  var_dump($_GET);
?>
```

Then, for any request with characters after the / following the hostname, e.g., https://cstutoring.ca/Hello/Alice, the characters would be displayed in an output of the following nature:

```
 array(1) { ["url"]=> string(11) "Hello/Alice" } 
```

We can now use the 'url' value to enable routing within the MVC application.
