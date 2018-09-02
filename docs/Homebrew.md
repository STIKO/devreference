##Install `homebrew`
[Install](https://brew.sh)
##Instal Location in Mac
```bash
/usr/local/Cellar/
```
##Link brew packages
To use `php@7.*` link new installed php using home-brew
```bash
which php
```
If you see this it's the stock version

	/usr/bin/php

If you see this you are using the Homebrew version

	/usr/local/bin/php

**To fix it reinstall and relink php using Homebrew:**

Reinstall PHP 7.1
```bash
brew reinstall php@7.1
```
check overwriting links
```bash
brew link --overwrite --force --dry-run php@7.1
```
Overwrite
```bash
brew link --overwrite --force php@7.1
```

Check if you're using homebrew's PHP
```bash
which php
```
```bash
php -v
```

If there is any missing extensions, install them
```bash
brew reinstall php71-xdebug php71-imagick
```

To have launchd start php@7.1 now and restart at login:
```bash
brew services start php@7.1
```
