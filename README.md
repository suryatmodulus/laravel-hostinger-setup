# laravel-hostinger-setup
A guide to setup Laravel 5.8 on hostinger shared hosting


# Steps:

1. create a .htaccess file in your root directory and copy the following content
```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_URI} !^public
  RewriteRule ^(.*)$ public/$1 [L]
</IfModule>
```
2. create an application in hostinger
3. Enable ssh access
4. login via ssh
5. cd public_html && rm default.php
6. copy entire content of your application including hidden files into this public_html folder
7. run cmd --> chmod -R 777 bootstrap/cache
8. run cmd --> chmod -R 777 storage
