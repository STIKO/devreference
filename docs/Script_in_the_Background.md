##Getting a Python script to run in the background (as a service) on boot
Run
`sudo nano /etc/init/TheNameOfYourDaemon.conf`

Add the following:
```text
description "My Daemon Job"
author "Your Name"
start on runlevel [2345]

pre-start script
  echo "[`date`] My Daemon Starting" >> /var/log/TheNameOfYourDaemonJobLog.log
end script

exec /bin/sh TheNameOfYourScript.sh > /dev/null &
```

Save it and confirm it looks ok:

```bash
init-checkconf /etc/init/TheNameOfYourDaemon.conf
```

Now reboot the machine:
```bash
sudo reboot
```
Now when you boot up your system, you can see the log file stating that your Daemon is running:
```bash
cat  /var/log/TheNameOfYourDaemonJobLog.log
```
Now you may start/stop/restart/get the status of your Daemon via:
restart: this will stop, then start a service
```bash
sudo service TheNameOfYourDaemonrestart restart
```
start: this will start a service, if it's not running
```bash
sudo service TheNameOfYourDaemonstart start
```
stop: this will stop a service, if it's running
```bash
sudo service TheNameOfYourDaemonstop stop
```
status: this will display the status of a service
```bash
sudo service TheNameOfYourDaemonstatus status
```