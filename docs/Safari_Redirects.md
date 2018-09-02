##Safari Always Redirects `localhost` to `https`
```bash
sudo killall nsurlstoraged
rm -f ~/Library/Cookies/HSTS.plist
launchctl start /System/Library/LaunchAgents/com.apple.nsurlstoraged.plist
```