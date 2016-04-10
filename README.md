# RemediPi

The purpose of this Raspberry Pi 2 Hardware Quickstart is to provide a fullstack codebase for building apps.

### Installation

[1. Download Ubuntu Mate](https://ubuntu-mate.org/raspberry-pi/)

[2. Write Image to SD card Via Mac Terminal](http://elinux.org/RPi_Easy_SD_Card_Setup)

[3. Resize File System](https://ubuntu-mate.org/raspberry-pi/)

[4. Setup HTTP and SSH Tunnels](https://ngrok.com/)

5. Start Hubot Script

```
#!/bin/sh

echo 'Remedi Pi is waking up...';

export HUBOT_FIREBASE_SECRET=YOUR_SECRET
export HUBOT_FIREBASE_APP_URL=https://YOUR_APP.firebaseio.com/hubot

cd RxRemedi;

FIREBASE_URL=$HUBOT_FIREBASE_APP_URL FIREBASE_SECRET=$HUBOT_FIREBASE_SECRET bin/hubot -n RxRemedi --adapter shell

exec $SHELL;
```

5. Ubuntu Mate Boot Up Scripts

System > Personal > Startup Applications or ~/.config/autostart

Start Hubot

```
[Desktop Entry]
Type=Application
Exec=mate-terminal -e "bash -c 'cd /home/remedi-admin/';'./start-hubot.sh';'exec /bin/bash'"
Hidden=false
X-MATE-Autostart-enabled=true
Name[en_US]=Start Hubot
Name=Start Hubot
Comment[en_US]=
Comment=
```

Create HTTP Tunnel for Web Traffic

```
[Desktop Entry]
Type=Application
Exec=mate-terminal -e "bash -c 'cd /home/remedi-admin/';'./ngrok http --hostname=YOUR_HOST 8080\n';'exec /bin/bash'"
Hidden=false
X-MATE-Autostart-enabled=true
Name[en_US]=Start ngrok http
Name=Start ngrok http
Comment[en_US]=
Comment=
```

Create TCP Tunnel for SSH

```
[Desktop Entry]
Type=Application
Exec=mate-terminal -e "bash -c 'cd /home/remedi-admin/';'./ngrok tcp --remote-addr N.tcp.ngrok.io:YOUR_PORT 22\n';'exec /bin/bash'"
Hidden=false
X-MATE-Autostart-enabled=true
Name[en_US]=Start ngrok tcp
Name=Start ngrok tcp
Comment[en_US]=
Comment=
```
