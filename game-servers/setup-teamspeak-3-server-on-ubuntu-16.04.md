---
description: >-
  A quick guide to setup Teamspeak 3 server on Ubuntu 16.04, Ubuntu 14.04,
  CentOS 6, CentOS 7, Debian 7 & Debian 8.
---

# Setup Teamspeak 3 Server on Linux

## Introduction

A Teamspeak server is a piece of VoIP software which allows users to communicate with each other via speech. Teamspeak consists of two applications: a client and a server.

The client application is the program that you use on your computer to log into teamspeak. It can be downloaded from the [download page on the official website](https://www.teamspeak.com/en/downloads). Download the client for the operating system that you are using.

The server application is the application that brings each client together. It is in charge of processing the VoIP data and handling messages between you and your friends.

This guide will explain the basics of setting up a TeamSpeak 3 server on Linux \(Debian, CentOS & Ubuntu Distributions\).

## Prerequisites

* A VPS running Ubuntu / Debian / CentOS.
* Teamspeak client software installed on your computer.
* An initial server setup for:
  * [Ubuntu](../virtual-private-servers/introduction-to-nginx-and-lemp-on-ubuntu/initial-server-setup-with-ubuntu.md)
  * CentOS
  * Debian

## **Step 1 - Adding User For Teamspeak 3 Server**

First, create a new user with your desired name, we will use the name "teamspeak" for this guide.

### Ubuntu / Debian

```bash
adduser --disabled-login teamspeak
```

### CentOS

```bash
useradd teamspeak
passwd teamspeak
```

## **Step 2 - Downloading Latest Version of Teamspeak 3 Server**

Get the latest TeamSpeak 3 server files for 64-bit Linux. Check their website, a new version may be available for all the distributions.

```bash
wget http://dl.4players.de/ts/releases/3.3.0/teamspeak3-server_linux_amd64-3.3.0.tar.bz2
```

## **Step 3 - Extracting the tar.bz2**

Extract the archive for all the distributions.

```bash
tar xvf teamspeak3-server_linux_amd64-3.3.0.tar.bz2
```

This will create a new folder in the root directory called: `teamspeak3-server_linux_amd64`

## **Step 4 - Moving the Files to Home Directory of Teamspeak**

Move the extracted files to the `teamspeak` user's home directory then remove the extracted folder and downloaded archive.

```text
cd teamspeak3-server_linux_amd64 && mv * /home/teamspeak && cd .. && rm -rf teamspeak3*
```

Accept the license agreement:

```text
touch /home/teamspeak/.ts3server_license_accepted
```

## **Step 5 - Setting up Ownership for user Teamspeak**

Change ownership of the TeamSpeak 3 server files.

```text
chown -R teamspeak:teamspeak /home/teamspeak
```

## **Step 6 - Setting up start script**

### **Ubuntu 16.04 / Debian 8 / CentOS 7 or Higher**

Make the TeamSpeak 3 server start on boot. Use your favorite editor to make a new file called `teamspeak.service` in `/lib/systemd/system/`.

```bash
nano /lib/systemd/system/teamspeak.service
```

Paste this content into it:

{% code-tabs %}
{% code-tabs-item title="/lib/systemd/system/teamspeak.service" %}
```bash
[Unit]
Description=TeamSpeak 3 Server
After=network.target

[Service]
WorkingDirectory=/home/teamspeak/
User=teamspeak
Group=teamspeak
Type=forking
ExecStart=/home/teamspeak/ts3server_startscript.sh start
ExecRestart=/home/teamspeak/ts3server_startscript.sh stop
ExecStop=/home/teamspeak/ts3server_startscript.sh stop
PIDFile=/home/teamspeak/ts3server.pid
RestartSec=15
Restart=always

[Install]
WantedBy=multi-user.target
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Once you are done, save the file and close the editor. Now we will activate the script so that it will start on boot.

This makes to systemd recognize the file we just created.

```bash
systemctl --system daemon-reload
```

Enable the service.

```bash
systemctl enable teamspeak.service
```

Start the TeamSpeak server.

```bash
systemctl start teamspeak.service
```

Once you've started the server, you can check that it's running with this command.

```bash
systemctl status teamspeak.service
```

### Ubuntu 14.04 / Debian 7 or Lower

Make Teamspeak3 start on boot up. For this, we will need to create a symlink to the script which was included in the archive that we downloaded earlier.

```bash
sudo ln -s /usr/local/teamspeak/ts3server_startscript.sh /etc/init.d/teamspeak
sudo update-rc.d teamspeak defaults
```

Now all that is left to do is to start your Teamspeak server!

```bash
sudo service teamspeak start
```

On your terminal, you will see a screen with the query username/password and a privilege key - be sure to write this information down as you will need it to administer your server.

### CentOS 6 or Lower

 Now we need to create the script in the /etc/init.d folder:

```bash
nano /etc/init.d/teamspeak
```

 Once you are in the file paste the following code into the file by right clicking the mouse.

{% code-tabs %}
{% code-tabs-item title="/etc/init.d/teamspeak" %}
```bash
#!/bin/sh
# chkconfig: 2345 99 10
USER="teamspeak"
TS3='/home/teamspeak/'
STARTSCRIPT="$TS3/ts3server_startscript.sh"
cd $TS3
case "$1" in
'start')
su $USER -c "$STARTSCRIPT start"
;;
'stop')
su $USER -c "$STARTSCRIPT stop"
;;
'restart')
su $USER -c "$STARTSCRIPT restart"
;;
'status')
su $USER -c "$STARTSCRIPT status"
;;
*)
echo "Usage $0 start|stop|restart|status"
esac
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Click Ctrl + O to save the file then Ctrl + X to exit the file. We can then set the file permission so it will work properly.

```bash
chmod 755 /etc/init.d/teamspeak
```

Now we need to add the service so it will restart when the server is restarted. Enter the following commands and then restart the server.

```bash
chkconfig --add teamspeak
chkconfig --level 2345 teamspeak on
```

Once the server restarts connect to teamspeak and make sure everything restarted. You can also check the status through command line by using the following command.

```bash
service teamspeak status
```

## **Step 7 - Retrieving Privilege Key**

When you first try to connect to your TeamSpeak server, you may be prompted to use a privilege key. This privilege key allows to administrate your TeamSpeak server. To get this privilege key, use the following command:

```text
cat /home/teamspeak/logs/ts3server_*
```

At bottom you'll see something that looks like this:

```text
--------------------------------------------------------
ServerAdmin privilege key created, please use the line below
token=****************************************
--------------------------------------------------------
```

Replace the stars with your unique token, and enter it into your TeamSpeak client. You'll see a prompt telling you that the privilege key was successfully used.

## **Optional: Firewall**

If you are using the built-in firewall that was included with the Ubuntu installation then `iptables` is your firewall. You may need to forward the following ports to allow connections to your TeamSpeak 3 Server.

```bash
iptables -A INPUT -p udp --dport 9987 -j ACCEPT
iptables -A INPUT -p udp --sport 9987 -j ACCEPT
iptables -A INPUT -p tcp --dport 30033 -j ACCEPT
iptables -A INPUT -p tcp --sport 30033 -j ACCEPT
iptables -A INPUT -p tcp --dport 10011 -j ACCEPT
iptables -A INPUT -p tcp --sport 10011 -j ACCEPT
```

## Conclusion

Congratulations! You've successfully created a Teamspeak Server. You can connect to it with the [Teamspeak Client](https://www.teamspeak.com/en/downloads.html#client).

Have fun!

