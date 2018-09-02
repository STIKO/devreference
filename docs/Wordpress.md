##Default host

To not update your DB everytime you move to `local` or `staging`, add these lines to `wp-config.php`
```php
define( 'WP_SITEURL', 'http://'.$_SERVER['HTTP_HOST']);
define( 'WP_HOME', WP_SITEURL );
```