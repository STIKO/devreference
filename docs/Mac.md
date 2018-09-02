##View All Users & Accounts on a Mac
```bash
$dscl . list /Users
```
##View All Users & Accounts on a Mac
```bash
dscl . list /Users
```

##Show All User Accounts, User Directories, & User GECOS Info on a Mac
```bash
dscacheutil -q user
```

##Show User Accounts Only
```bash
$dscl . list /Users | grep -v '_'
```
##Show All User Accounts, User Directories, & User GECOS Info on a Mac
```bash
$dscacheutil -q user
```

##Get User Info
To get user `creationTime`, `failedLoginCount` and `failedLoginTimestamp`
```bash
dscl . read /Users/ahmedalsammarraie accountPolicyData
```
##Format usb flash drive from terminal
```bash
diskutil eraseDisk JHFS+ Emptied /dev/disk6s2
```
FTP
```bash
diskutil eraseDisk FTP32 Emptied /dev/disk6s2
```
##Create Hidden User
```bash
dscl /Local/Default -create /Users/hidden
```
Create home directory to it
```bash
dscl /Local/Default -create /Users/hidden NFSHomeDirectory /Users/hidden
```
Give it a real name
```bash
dscl /Local/Default -create /Users/hidden RealName "real_name"
```
Set primary group
```bash
dscl /Local/Default -create /Users/hidden PrimaryGroupID 80
```
User shell
```bash
dscl /Local/Default -create /Users/hidden UserShell /bin/bash
```
Unique ID
```bash
dscl /Local/Default -create /Users/hidden UniqueID 499
```
Set password
```bash
dscl /Local/Default -passwd /Users/hidden 'PASSWORD' ;
```
Hide it
```bash
dscl . create /Users/hidden IsHidden 1 ;
```
##Allow Remote Management
```bash
sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -activate -configure -allowAccessFor -allUsers -privs -all -setmenuextra -menuextra yes
systemsetup -f -setremotelogin on ;
defaults write /Library/Preferences/com.apple.RemoteManagement LoadRemoteManagementMenuExtra -bool false
```
##Find ip’s and mac address’s on network
```bash
arp -an
```
##Temp Files Location
```text
~/Library/Caches/
```
##Force Signout iCloud
```bash
defaults delete MobileMeAccounts
```

**Remove iMessage history**

Possibly:
```bash
rm ~/Library/Preferences/*.plist
```
Instead of:
```bash
cd ~/Library/Preferences
rm com.apple.ids.service.com.apple.madrid.plist
rm com.apple.ids.service.com.apple.private.alloy.sms.plist
rm ByHost/com.apple.identityservices.idstatuscache.5A488A33-7FF1-56F5-A3F6-CBC792D5C705.plist
```

Then:
```bash
rm ~/Library/Messages/chat.db*
rm -rf ~/Library/Messages/Archive
rm -rf ~/Library/Messages/Attachments
```
**Restart Mac**

```bash
sudo shutdown -r now
```