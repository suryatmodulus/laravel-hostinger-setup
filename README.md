# laravel-hostinger-setup
A guide to setup Laravel 5.8 on hostinger shared hosting


# Steps for Deployment :

1. Create a .htaccess file in the root directory of your laravel application and copy the following content to it.
```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_URI} !^public
  RewriteRule ^(.*)$ public/$1 [L]
</IfModule>
```
2. Create an application in hostinger
3. Enable ssh access
4. Login via ssh and run `cd public_html && rm default.php`
5. Zip all the files and folders of your laravel application (including hidden) and import to public_html folder and extract it
6. Set permissions for cache and storage folder by running following commands
```
chmod -R 777 bootstrap/cache && chmod -R 777 storage
````
7. Remove the symlink storage folder in public/ by running
```
rm -rf public/storage
```
8. Manually create symlink for storage folder (because Hostinger disables symlink() in PHP)
```
ln -s $HOME/domains/<domain_name>/storage/app/public $HOME/domains/<domain_name>/public/storage
```
**Replace <domain_name> with the domain name of your website (example : beeware.com)**  

# Steps for Deployment with Github :

1. Create a .htaccess file in the root directory of your laravel application and copy the following content to it.
```
<IfModule mod_rewrite.c>
  RewriteEngine on
  RewriteCond %{REQUEST_URI} !^public
  RewriteRule ^(.*)$ public/$1 [L]
</IfModule>
```
2. Remove the .gitignore from the application root by running
`cd to-your-application && rm .gitignore`
3. Create a repository and add all the files to that
4. Create an application in hostinger
5. Enable ssh access
6. Login via ssh and run `rm public_html/default.php`
7. Run `git clone your-repository-link public_html` (example: `git clone https://github.com/suryatmodulus/laravel-hostinger-setup.git public_html`)
8. Set permissions for cache and storage folder by running following commands
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
**Replace <domain_name> with the domain name of your website (ex : beeware.com)**
