# Testing your site before ‘go-live’ by editing your hosts file

We all know the importance of testing your site after a migration to your hosting account.  More often than not we wish to do this prior to updating the domain’s DNS nameservers to Brixly.   We have a few options that allow us to do this – via the control panel, as well as by modifying your local PC’s hosts file.

### The cPanel \(Linux\) Temporary URL: <a id="The_cPanel_(Linux)_Temporary_URL:"></a>

Every cPanel user’s main domain is accessible via the IP address of the server and their username.  For example:

```text
<a href="http://1.1.1.1/~username">http://1.1.1.1/~username</a>
```

\(You will need to replace the “IP Address” with the actual IP Address of the server, as well as “username” with your cPanel user to utilize this\).

The following addresses will bring you to the contents of your main public\_html folder, you can append subfolders to the URLs for further testing if needed, for example:

```text
<a href="http://1.1.1.1/~username/subfolder/anotherfolder/yetanotherfolder/">http://1.1.1.1/~username/subfolder/anotherfolder/yetanotherfolder/</a>
```

### How To Change your Computer’s Hosts File: <a id="How_To_Change_your_Computer&#x2019;s_Hosts_File:"></a>

Temporary URLs work well in most cases, but in other cases some content management systems rely heavily on DNS and redirections in order to function properly, making testing via temporary URLs difficult as clicking links will take you to the domain name again, itself.  In cases like this – we update the hosts file for testing on your local PC.

One thing to keep in mind, regardless of which operating system you use at home, you can simply add your host information to the bottom of the file – in the following format:

```text
X.X.X.X   domain.com
X.X.X.X   www.domain.com
```

X.X.X.X will be the IP address we are going to force your computer \(and only your computer\) to resolve the domain to. This will be the IP address assigned to the domain name.  Domain.com will be the domain name to test prior to updating the DNS.

Another thing to keep in mind when testing your site using the hosts file method- after updating your hosts file, **you will need to clear the cache and cookies from your web browser and restart the browser in order for things to take full effect.  In some instances, you may need to flush your DNS cache on the local system as well.**

#### Updating a Hosts File on Windows: <a id="Updating_a_Hosts_File_on_Windows:"></a>

Go to Start  -&gt;  All Programs  -&gt;  Accessories

Right click on Notepad, and select “Run as Administrator”

Click “Continue” at the UAC prompt.

In the notepad application – From the toolbar, go to   File -&gt; Open

Open the Following File:

```text
C:\Windows\System32\drivers\etc\hosts
```

\(This path may vary based on your drive/installation configuration, and you may need to choose the file type to open from the drop down menu as “All Files” in order to see your hosts file\).

Add your new host entry to the bottom of the file and save.

[![change\_hosts\_file](http://blog.arvixe.com/wp-content/uploads/2013/02/change_hosts_file-300x233.png)](http://blog.arvixe.com/wp-content/uploads/2013/02/change_hosts_file.png)

_figure 2.  A Windows 7 hosts file with an example entry added so that mydomain.com resolves to the IP of 1.2.3.4_

#### Updating a Hosts File in Linux: <a id="Updating_a_Hosts_File_in_Linux:"></a>

Open up your favourite terminal application \(Most flavours store the default terminal application in the Accessories folder\).  Also, in this example, we are using the text editor called “nano” which is pre-installed on most Linux distributions.  You may also use other text editors such as vim or emacs if you wish.

If you are already logged in as  user root, run:

```text
nano /etc/hosts
```

If you are logged in as a non-root user, run:

```text
sudo  nano /etc/hosts
```

Then authenticate with your password to grant root access.

Once the text editor application opens, add your new host entry to the bottom of the file and save.

#### Updating a Hosts File on a Mac: <a id="Updating_a_Hosts_File_on_a_Mac:"></a>

You will need to launch your Terminal, which you can search for using Spotlight, or you may also access this via Applications/Utilities

Once the terminal application has launched, type the following into the terminal command line:

sudo nano /private/etc/hosts

Enter the Administrator password.

After the file has opened, add your new host entry to the bottom of the file and save.

**Again, make sure you clear the cache from your browser and in some cases the DNS cache may need to be flushed as well.**

_After you update the DNS for your site, make sure to remove any host entries that you may have added during the process to ensure the domain is resolving in the same manner on your local system as other users on the internet!_

