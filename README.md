# pgproc-www
Access PostgresSQL procedures through HTTP

## Prerequisites:

 - pgproc module (https://github.com/actimeo/pgproc)
 - PostgreSQL server 9.1 or higher
 - PHP 5.5 or higher

## Install

- Install necessary PHP modules
```sh
$ composer install
```

- copy `config.inc.php.sample` to `config.inc.php`
- copy `config.sh.sample` to `config.sh`
- edit these 2 files with the name and credentials of your database you want to access

- serve the subdirectory backend/htdocs with your preferred web server
- Apache2 configuration:
```
<VirtualHost *:80>
  [...]
  Alias /pg "/path/to/pgproc-www/htdocs"
  <Directory "/path/to/pgproc-www/htdocs">
      Options Indexes MultiViews FollowSymlinks
      AllowOverride None
      Order allow,deny
      Allow from all
      RewriteEngine on
      RewriteCond %{REQUEST_FILENAME} !-d
      RewriteCond %{REQUEST_FILENAME} !-f
      RewriteRule ^(.*)$ /pg/index.php?o=$1 [L,QSA]
  </Directory>
</VirtualHost>
```
