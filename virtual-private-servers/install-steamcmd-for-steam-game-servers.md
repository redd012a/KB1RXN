---
description: >-
  A detialed overview on how to install SteamCMD for Game Servers in any
  environment.
---

# Installing SteamCMD for Steam Game Servers



## SteamCMD

The Steam Console Client or SteamCMD is a command-line version of the Steam client. Its primary use is to install and update various dedicated servers available on Steam using a command-line interface. It works with games that use the [SteamPipe](https://developer.valvesoftware.com/wiki/SteamPipe) content system. All games have been migrated from the deprecated [HLDSUpdateTool](https://developer.valvesoftware.com/wiki/HLDSUpdateTool) to SteamCMD.

## Downloading SteamCMD

### Windows

1. Create a folder for SteamCMD.

    For example

   ```text
    C:\steamcmd
   ```

2. Download SteamCMD for Windows: [https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip](https://steamcdn-a.akamaihd.net/client/installer/steamcmd.zip)
3. Extract the contents of the zip to the folder.

### Linux

Create a user account named steam to run SteamCMD safely, isolating it from the rest of the operating system. Do not run steamcmd while operating as the root user - to do so is a security risk.

1. As the root user, create the steam user:

   ```bash
    useradd -m steam
   ```

2. Go into its home folder:

   ```bash
    cd /home/steam
   ```

   **Package from repositories**

3. It's recommended to install the SteamCMD package from your distribution repositories, if available:

   Ubuntu/Debian

   ```bash
    sudo apt-get install steamcmd
   ```

   RedHat/CentOS

   ```bash
    yum install steamcmd
   ```

   Arch Linux: install [steamcmd from the AUR](https://aur.archlinux.org/packages/steamcmd/).

4. Link the steamcmd executable:

   ```bash
    ln -s /usr/games/steamcmd steamcmd
   ```

   **Manually**

5. Before you begin, you must first install the dependencies required to run SteamCMD:

   Ubuntu/Debian 64-Bit

   ```bash
    sudo apt-get install lib32gcc1
   ```

   RedHat/CentOS

   ```bash
    yum install glibc libstdc++
   ```

   RedHat/CentOS 64-Bit

   ```bash
    yum install glibc.i686 libstdc++.i686
   ```

6. As the root user, escalate to the steam user:

   ```bash
    su - steam
   ```

    If you're not logging in as root and you instead use sudo to perform administration, escalate to the steamuser as follows:

   ```bash
    sudo -iu steam
   ```

7. Create a directory for SteamCMD and switch to it.

   ```bash
    mkdir ~/Steam && cd ~/Steam
   ```

8. Download and extract SteamCMD for Linux.

   ```bash
    curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz" | tar zxvf -
   ```

### OS X

1. Open Terminal.app and create a directory for SteamCMD.

   ```bash
    mkdir ~/Steam && cd ~/Steam
   ```

2. Download and extract SteamCMD for OS X.

   ```bash
    curl -sqL "https://steamcdn-a.akamaihd.net/client/installer/steamcmd_osx.tar.gz" | tar zxvf -
   ```

## Running SteamCMD

On first run, SteamCMD will automatically update and enter you into a **Steam** &gt; **prompt**. Type **help** for more information.

### Windows

Open a Command Prompt and start SteamCMD.

```bash
cd C:\steamcmd
steamcmd
```

### Linux/OS X

Open a terminal and start SteamCMD.

If you installed it using the package from repositories:

```bash
cd ~
steamcmd
```

If you installed it manually:

```bash
cd ~/Steam
./steamcmd.sh
```

## SteamCMD Login

### Anonymous

To download most game servers, you can login anonymously.

```bash
login anonymous
```

### With a Steam account

Some servers require you to login with a Steam Account.

￼&gt; **Note:** For security reasons it is recommended that you create a new Steam account just for your dedicated servers.

￼&gt; **Note:** A user can only be logged in once at any time \(counting both graphical client as well as SteamCMD logins\).

```bash
login <username>
```

Next enter your password.

If Steam Guard is activated on the user account, check your e-mail for a Steam Guard access code and enter it. This is only required the first time you log in \(as well as when you delete the files where SteamCMD stores the login information\).

You should see a message stating that you have successfully logged in with your account.

## Downloading an app

1. Start SteamCMD and log in.
2. Set your app install directory. \(Note: use forward slashes for Linux/OS X and backslashes for Windows.\)

   ```text
    force_install_dir <path>
   ```

   e.g. a directory named cs\_go inside the current directory:

   ```text
    force_install_dir ./cs_go/
   ```

   **For Windows:** force\_install\_dir c:\cs\_go\

3. Install or update the app using the `app_updatecommand` \(supplying a [Steam Application ID](https://developer.valvesoftware.com/wiki/Steam_Application_IDs)\). Please check here for the dedicated server list: [Dedicated server list](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List). To also validate the app, add `validate` to the command. To download a beta branch, use the `-beta <betaname>` option – for example, the HLDS beta branch is named `beta` and the SrcDS beta branch is named `prerelease`. Some beta branches are protected by a password; to be able to download from them, also add the `-betapassword <password>` option.

   ```bash
    app_update <app_id> [-beta <betaname>] [-betapassword <password>] [validate]
   ```

   HLDS is a special case: the App ID is always 90 and a mod must be chosen first. This is done by setting the app config option mod to the requested value.

   ```text
    app_set_config <app_id> <option_name> <option_value>
   ```

   Example: Install and validate the Counter Strike: Global Offensive dedicated server:

   ```text
    app_update 740 validate
   ```

   Example: Install and validate HLDS with Team Fortress Classic:

   ```text
    app_set_config 90 mod tfc app_update 90 validate
   ```

   ￼**Bug:** HLDS \(appid 90\) currently requires multiple runs of the `app_update` command before all the required files are successfully installed. Simply run `app_update 90 validate` multiple times until no more updates take place.

   Example: Install and validate beta version of HLDS \(Half-Life\):

   ```text
    app_update 90 -beta beta validate
   ```

   Example: install and validate beta version of the Counter Strike: Source dedicated server:

   ```text
    app_update 232330 -beta prerelease validate
   ```

   Example: install and validate a private beta version of the Natural Selection 2 dedicated server \(name alpha, password natsel\): \[beta name\] is the name of the private beta branch \[beta code\] is the password for the private beta branch

   ```text
    app_update 4940 -beta alpha -betapassword natsel validate
   ```

4. Once finished, type `quit` to properly log off of the Steam servers.

   ```text
    quit
   ```

### Validate

```text
validate
```

Validate is a command that will check all the server files to make sure they match the SteamCMD files. This command is useful if you think that files may be missing or corrupted.

￼&gt; **Note:** Validation will overwrite any files that have been changed. This may cause issues with customized servers. For example, if you customize `mapcycle.txt`, this file will be overwritten to the server default. Any files that are not part of the default installation will not be affected.

It is recommended you use this command only on initial installation and if there are server issues.

### Supported Servers

A list of known servers that use SteamCMD to install is available on the [Dedicated Servers List](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List) page. Note that any extra commands listed need to be executed before the `app_update` line.

## Automating SteamCMD

There are two ways to automate SteamCMD. \(Replace `steamcmd` with `./steamcmd.sh` on Linux/OS X.\)

### Command line

￼&gt; **Note:** When using the `-beta` option on the command line, it must be quoted in a special way, such as `+app_update "90 -beta beta"`.

￼&gt; **Note:** If this does not work, try putting it like `"+app_update 90 -beta beta"` instead.

Append the commands to the command line prefixed with plus characters, e.g.:

```text
steamcmd +login anonymous +force_install_dir ../csgo_ds +app_update 740 +quit
```

To install a specific game mod for HL1, such as Counter-Strike: Condition Zero:

```text
steamcmd +login anonymous +force_install_dir ../czero +app_set_config 90 mod czero +app_update 90 +quit
```

For a game that requires logins, like Killing Floor:

```text
steamcmd +login <username> <password> +force_install_dir c:\KFServer\ +app_update 215350 +quit
```

### Creating a script

1. Put your SteamCMD commands in a text file. \(You may add comments which start with `//`.\) Example:

   ```bash
    // update_csgo_ds.txt
    //
    @ShutdownOnFailedCommand 1 //set to 0 if updating multiple servers at once
    @NoPromptForPassword 1
    login <username> <password> //for servers which don't need a login
    //login anonymous
    force_install_dir ../csgo_ds 
    app_update 740 validate 
    quit
   ```

2. Run SteamCMD with the `+runscript` option, referring to the file you created previously. Example:

   ```text
    steamcmd +runscript csgo_ds.txt
   ```

## Cross-Platform Installation

It is possible to choose the platform for which SteamCMD should download files, even if it isn't the platform it is currently running on. This is done using the `@sSteamCmdForcePlatformType` variable. \(Yes, those are two "s"es at the beginning of the variable name.\) For example, to download the Windows CSGO dedicated server on Linux, you can run the following command:

```text
./steamcmd.sh +@sSteamCmdForcePlatformType windows +login anonymous +force_install_dir ../csgo_ds +app_update 740 validate +quit
```

or use the following script:

```text
@ShutdownOnFailedCommand 1
@NoPromptForPassword 1
@sSteamCmdForcePlatformType windows
login anonymous
force_install_dir ../csgo_ds
app_update 740 validate
quit
```

The supported values are `windows`, `macos` and `linux`.

## Windows Software/Scripts

### condenser

[condenser](https://github.com/sympatovit/condenser) is a bootstrapper for installing, configuring, & launching Steam dedicated server apps.

### SteamCMD AutoUpdater

Install and automatically update any game server

GitHub Repo: [https://github.com/C0nw0nk/SteamCMD-AutoUpdate-Any-Gameserver](https://github.com/C0nw0nk/SteamCMD-AutoUpdate-Any-Gameserver)

### SteamCMD GUI

This tool allows the user to use SteamCMD on Windows without command lines and/or batch files.

GitHub Repo: [https://github.com/DioJoestar/SteamCMD-GUI](https://github.com/DioJoestar/SteamCMD-GUI)

### SteamCMD Guardian 1.2

View and download here: [http://pastebin.com/BRUbsGQh](http://pastebin.com/BRUbsGQh)

## Linux Scripts

### Linux Game Server Managers

LinuxGSM is the command line tool for quick, simple deployment and management of dedicated game servers, using SteamCMD.

#### Features

* Backup
* Console
* Details
* Installer \(SteamCMD\)
* Monitor
* Alerts \(Email, Pushbullet\)
* Update \(SteamCMD\)
* Start/Stop/Restart server

#### Supported Servers

There are now 70+ different game servers supported and rising. For a full list visit the website.

#### Links

Website: [https://gameservermanagers.com](https://gameservermanagers.com)

GitHub Repo: [https://github.com/GameServerManagers/LinuxGSM](https://github.com/GameServerManagers/LinuxGSM)

### SteamCMD Guardian 1.2

The following script was tested on Debian Wheezy.

View and download here: [http://pastebin.com/hcpMpmaZ](http://pastebin.com/hcpMpmaZ)

**Installation**

To make this script work, we need a location. Preferably you created a user \(e.g. steam\) with it's own home directory \(/home/steam\) and are logged in as it via SSH, tty or using su.

1. Make the file

   ```text
    nano updateserver.sh
   ```

2. Paste in the code
3. Modify the code, add `at least` 1 game to the `DL_SV*=` rows.
4. Close the file with `Ctrl`+`O`, followed by `↵ Enter` and concluding with `Ctrl`+`X`.
5. Give the file execute rights for the userchmod u+x ./updateserver.sh
6. Run the file

   ```text
    ./updateserver.sh
   ```

    The file will auto-download SteamCMD, update it and install all chosen games \(up to 4\). Run the file again to update the games.

## Known issues

### ERROR! Failed to install app 'xxxxxx' \(No subscription\)

If you get the 'No subscription' error, the game/server you are trying to download either requires a login or that you have purchased the game. You will therefore have to log in with a Steam username and password – if that doesn't help, you may need to purchase a copy of the game on Steam first. See [Dedicated Servers List](https://developer.valvesoftware.com/wiki/Dedicated_Servers_List).

> **Note:** For security reasons it is recommended that you create a new Steam account just for your dedicated servers.

For example

```text
steamcmd +login <username> <password>
```

### 32-bit libraries on 64-bit Linux systems

Since SteamCMD is a 32-bit binary, 32-bit libraries are required.

The following error may occur:

```text
steamcmd: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```

The resolution depends on your distro:

#### Debian based distributions \(Ubuntu, Mint, etc.\)

```text
sudo apt-get install lib32stdc++6
```

￼&gt; **Note:** ia32-libs are not required to install SteamCMD; lib32gcc1 is enough.

With **Debian 7 "Wheezy"** you may encounter this error:

```text
The following packages have unmet dependencies: ia32-libs : Depends: ia32-libs-multiarch but it is not installable E: Unable to correct problems, you have held broken packages.
```

To fix this, do the following:

```text
dpkg --add-architecture i386
apt-get update
apt-get install lib32gcc1
```

#### Red Hat based distributions \(RHEL, Fedora, CentOS, etc.\)

```text
yum install glibc.i686 libstdc++.i686
```

#### Arch Linux

Don't forget to first enable the [multilib repository](https://wiki.archlinux.org/index.php/Multilib).

```text
pacman -S lib32-gcc-libs
```

### Login Failure: No Connection

On linux servers, you may experience a "Login Failure: No Connection" error. This is related to missing iptables rules. You will want something along these lines:

```text
iptables -A INPUT -p udp -m udp --sport 27000:27030 --dport 1025:65355 -j ACCEPT iptables -A INPUT -p udp -m udp --sport 4380 --dport 1025:65355 -j ACCEPT
```

The port list is found here: [https://support.steampowered.com/kb\_article.php?ref=8571-GLVN-8711&l=english](https://support.steampowered.com/kb_article.php?ref=8571-GLVN-8711&l=english)

On Windows servers, you may experience "SteamUpdater: Error: Download failed: http error 0" and "SteamUpdater: Error: Steam needs to be online to update. Please confirm your network connection and try again.". This is usually fixed by checking "Automatically detect settings" in IE \(Internet Explorer\) through the lan settings in the Internet option menu. 1. Open Internet Explorer \(IE\). 2. Click on **Tools** → **Internet Options** 3. Click on the **Connections** tab 4. At the bottom, you should see **Local Area Network \(LAN\) Settings**. 5. Check the first box \(**Automatically detect settings**\) 6. Hit **OK**, and **Apply**. Try running the SteamCMD again; if it still doesn't work. try lowering your **Internet Security level zone** to medium or lower. You can find that in the **Security** tab in **Internet Options**.

### SteamCMD startup errors

#### Unable to locate a running instance of Steam

You may get the following error when starting a server with Linux:

```text
[S_API FAIL] SteamAPI_Init() failed; unable to locate a running instance of Steam, or a local steamclient.dll.
```

Resolve the issue by linking `steamclient.so` to the `~/.steam/sdk32/steamclient.so` directory:

```text
ln -s steamcmd/linux32/steamclient.so ~/.steam/sdk32/steamclient.so
```

#### ulimit Linux startup error

Some users may get a `ulimit` error \(no permission/cannot open file\) while script is starting up. This error caused by a low setting of the `-nparameter` \(number of file descriptors\) of `ulimit`. SteamCMD uses standard commands inside of the initialization shell script to change the `ulimitautomatically`, but some servers may forbid increasing `ulimit` values after startup \(or beyond a limit set by `root`\).

This can be fixed by changing the file descriptor number ulimit:

```text
ulimit -n 2048
```

If an error appears \(no permission\), you will have to log in as root to change the parameter. To check the current setting, type `ulimit -a`; the system will reply with many rows, you need to find one:

```text
open files (-n) 1024
```

In this case,`1024` is the current value.

`root` can also modify the limits in the `/etc/security/limits.conf` file.

In most instances you will simply get a warning message however it will not stop SteamCMD from running.

### Only the HLDS engine is downloaded

When trying to download a HL1 mod like TFC, initially it only downloads the engine files of the HLDS, but not the mod. This happens with both the regular version and the beta. You may have to try multiple times until all the required files are downloaded, but once this is done, the files should update correctly next time.

Work-around for this issue here: [http://danielgibbs.co.uk/2017/10/hlds-steamcmd-workaround-appid-90-part-ii/](http://danielgibbs.co.uk/2017/10/hlds-steamcmd-workaround-appid-90-part-ii/)

Just deleting the appmanifest files, without downloading replacements from a third party, may work as well! You will get an error at first though, complaining that something went wrong, which is due to the deleted files.

On a side note, for some reason CS is always installed as well.

## See Also

* Source Dedicated Server
* Half-Life Dedicated Server
* Dedicated Servers List
* SteamCMDui

