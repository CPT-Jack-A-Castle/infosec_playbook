## ID: 800005

## HF

## Source: IDS

## Category: Malware

## Description: A suspected PHP file has been uploaded

## Objective Statement:
A HTTP POST request containing a file upload with a PHP extension or HTTP Attribute`Content-type: application/x-httpd-php` was detected.


PHP executes on the server side, back-end portion of a website.  It can be used to communicate with the database, validate login credentials and can execute system commands.


## Result Analysis:


PHP File Extensions to look for:
*.php 
*.PHP
*.Php (or any capital variation)
*.png.php
*.php;png
*.php%00.png
*.php2
*.php5

PHP Files contain "<?php " to tell the webserver to execute the contents as PHP.  Look for these characters as well as other PHP syntax.  Commands can be executed in SQL, this can look like:

```php
system("ls -al");

shell_exec("ls -al");

exec("ls -al");

system($_GET['cmd']);
```
The last line would be when the parameter is provided through the URL when calling and executing suspected malicious PHP.

```
http://www.dpi911.com/dvwa/execute.php?cmd=ls -al
```

*References for Futher Learning*
- https://www.owasp.org/index.php/Unrestricted_File_Upload
- https://www.owasp.org/index.php/Top_10_2007-Malicious_File_Execution


## Mitigation
- Sanitize user input by checking for both file extensions and file types (File Magic Number) 
- Restrict which users can upload files
- Do not check the file type using javascript as the clients can get around the detection
- Do all checks server side
- Use Web Application Firewall to detect and block
- https://www.owasp.org/index.php/Protect_FileUpload_Against_Malicious_File

## Data Query Code
- PHP file upload
- file upload atttack
- malicious file
- malware uploaded and execute
- php command execution, remote shell