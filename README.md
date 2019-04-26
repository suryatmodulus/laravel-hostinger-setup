# laravel-hostinger-setup
A guide to setup Laravel 5.8 on hostinger shared hosting


# Steps:

1. create a .htaccess file in the root directory of your laravel application and copy the following content to it.
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
5. run --> `cd public_html && rm default.php`
6. copy all the files and folders of your laravel application (including hidden) into this public_html folder
7. Set permissions to cache and storage folder by running following commands
```
chmod -R 777 bootstrap/cache && chmod -R 777 storage
````
9. Remove the symlink storage folder in public/ by running
```
rm -rf public/storage
```
10. Manually create symlink for storage folder (because Hostinger disables symlink() in PHP)
```
ln -s $HOME/domains/<domain_name>/storage/app/public $HOME/domains/<domain_name>/public/storage
```
**Replace <domain_name> with the domain name of your website ex : beeware.com**  
