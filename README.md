# Speedtest.net dashboard widget for pfSense

This new widget is made to replace a similar widget created in the past by Alon Noy. That widget however used the not official speedtest-cli that is no longer supported. The no longer supported version of speedtest-cli has a limitation that it can only list and connect 10 geographic chosen test servers which are in most cases never the best server for your tests. And also the test results are not the best when compared with the original speedtest-cli from speedtest.net.

![Screenshot](https://github.com/LeonStraathof/pfsense-speedtest-widget/blob/main/Widget-screenshot.png?raw=true)

## INSTALL

Goto https://www.speedtest.net/apps/cli
Click FreeBSD and find URL of newest version.
pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
(Use the URL found on the speedtest.net website and the FreeBSD version number in env ABI must match the version number in the URL)
There is a know conflict between the not offical speedtest-cli and the offical version from speedtest.net. You can not have both installed at the same time. See this reported issue: https://github.com/LeonStraathof/pfsense-speedtest-widget/issues/2
```	
env ABI=FreeBSD:13:x86:64 pkg add "https://install.speedtest.net/app/cli/ookla-speedtest-1.2.0-freebsd13-x86_64.pkg"
```
pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
```
speedtest --accept-license
```
pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
```
speedtest --accept-gdpr
```
pfSense-main-menu-->Diagnotics-->Command Prompt-->Upload File:
speedtest.widget.php

pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
```
mv -f /tmp/speedtest.widget.php /usr/local/www/widgets/widgets/
```
pfSense-main-menu-->Status-->Dashboard:
Add the speedtest widget.
	
## UNINSTALL

pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
```
pkg info | grep speedtest
```
pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
(use the package name found in the first step)	
```
pkg delete -y speedtest-1.2.0.84-1.ea6b6773cf
```
pfSense-main-menu-->Status-->Dashboard:
Remove the speedtest widget.

pfSense-main-menu-->Diagnotics-->Command Prompt-->Execute Shell Command:
```
rm -f /usr/local/www/widgets/widgets/speedtest.widget.php
```
