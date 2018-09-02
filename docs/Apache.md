##Enable/disable site apache2
Enable site
```bash
a2ensite [site]
```
Disable site
```bash
a2dissite [site]
```
##Activate rewrite on ubuntu
**Apache**
```bash
sudo a2enmod rewrite
```
##Redirect the home page via .htaccess
```
<IfModule mod_rewrite.c>
	RewriteEngine On
    RewriteBase /
    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteRule ^$ /index.php?pagename=home [QSA,L]
</IfModule>
```

##Enable override
Open file `/etc/apache/sites/available/00*.cnf` and add
```text
<Directory /var/www/html>
                Options FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
</Directory>
```s
