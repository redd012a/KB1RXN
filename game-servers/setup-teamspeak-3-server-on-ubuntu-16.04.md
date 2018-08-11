---
description: A quick guide to setup Teamspeak 3 server on Ubuntu 16.04
---

# Setup Teamspeak 3 server on Ubuntu 16.04

This guide, gives step-by-step to installing Teamspeak 3 \(3.0.13.6\) 64 bit server on Ubuntu 16.04 LTS. You can grab latest version [here](https://teamspeak.com/en/downloads).

**Step 1:**  
Login to SSH as root

**Step 2:**  
Run the below commands:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

{% hint style="info" %}
**Note:** During the `sudo apt-get upgrade` command, you maybe asked about the grub load. Press `Enter`
{% endhint %}

**Step 3:**  
Let create a user for the Teamspeak 3 server.

```bash
sudo adduser --disabled-login teamspeak
```

You will be asked for user information for teamspeak. Press Enter for all the questions.  
You will also be asked is the information correct. Press Enter.

**Step 4:**  
Type the following command

```bash
cd /home/teamspeak/;su teamspeak
```

**Step 5:**  
Run the following commands to download Teamspeak, extract it and tidy up.

```bash
wget http://dl.4players.de/ts/releases/3.3.0/teamspeak3-server_linux_amd64-3.3.0.tar.bz2
tar xvfj teamspeak3-server_linux_amd64-3.3.0.tar.bz2
cd teamspeak3-server_linux_amd64
cp * -R /home/teamspeak
cd ..
rm -r teamspeak3-server_linux_amd64
rm teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2

```

  
**Step 6:**  
Now we start the TS3 server

```bash
./ts3server_startscript.sh start
```

Make sure you copy and save the security token and Server Query Admin Account details, once the server has started.

**Step 6.1:**  
Press Enter. This will return to the command prompt.

**Step 7:**  
Now we need to stop the server and return to root, enter the below:

```bash
./ts3server_startscript.sh stop
exit
```

**Step 8:**  
Now we will create a restart script using systemd to restart it on boot.

Run the below command \(This should open a blank page\)

```bash
nano /lib/systemd/system/ts3server.service
```

**Step 8.1.**  
Copy the below and paste it:

{% code-tabs %}
{% code-tabs-item title="ts3server.service" %}
```bash
[Unit]
Description=Teamspeak Service
Wants=network.target

[Service]
WorkingDirectory=/home/teamspeak
User=teamspeak
ExecStart=/home/teamspeak/ts3server_minimal_runscript.sh
ExecStop=/home/teamspeak/ts3server_startscript.sh stop
ExecReload=/home/teamspeak/ts3server_startscript.sh restart
Restart=always
RestartSec=15

[Install]
WantedBy=multi-user.target
```
{% endcode-tabs-item %}
{% endcode-tabs %}

**Step 8.2:**  
Now we need to save it

Press `CTRL+X` together, then Press `Y`

**Step 9:**  
Now we need to enable it, by typing in the following command:

```bash
systemctl enable ts3server.service
```

**Step 9.1:**  
Type in the following to restart the server\)

```bash
reboot
```

**Step 10:**  
Reconnect to SSH, once the server has restarted and enter the following command:

```bash
systemctl status ts3server
```

**Step 10.1:**  
This should return an ouput look for:

```bash
Active: active `(running)`
```

**Step 10.2:**  
To return to the command prompt, you will need to:  
Press `Q`

