##Change php version
```bash
a2dismod php5
a2enmod php7.0
service apache2 restart
```
##Find `php.ini` File Path
```bash
php --ini | grep "Loaded Configuration" | sed -e "s|.*:\s*||"
```
