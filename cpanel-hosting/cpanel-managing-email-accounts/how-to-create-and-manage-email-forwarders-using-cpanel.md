# How to create and manage email forwarders using cPanel

Send a copy of any incoming email from one address to another. For example, forward **joe@example.com** to **joseph@example.com** so that you only have one inbox to check.

{% code-tabs %}
{% code-tabs-item title="Location under cPanel" %}
```text
cPanel >> Home >> Email >> Forwarders
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Overview

This interface allows you configure an email address to forward copies of incoming emails to another address. This is useful if, for example, you want to use one email address to check emails addressed to multiple accounts. You can also discard email or send \(pipe\) email to a program.

To manage forwarders for a specific domain on your account, select the desired domain from the _Managing_ menu.

Note:To manage forwarders for email accounts that use the [_BoxTrapper_](https://documentation.cpanel.net/display/68Docs/BoxTrapper) __feature _\(cPanel &gt;&gt; Home &gt;&gt; Email &gt;&gt; BoxTrapper\)_, use the _BoxTrapper Forward List_ feature.

## Email Account Forwarders

The _Email Account Forwarders_ table lists all of the email addresses that use a forwarder to redirect email to another address or service.

* To quickly find a specific email address, enter a keyword in the _Search_ text box and click _Go_.
* To view the route that a forwarded email takes, click _Trace_ in the _Functions_ next to that email address.
* To delete a forwarder, click _Delete_ next to that email address, and then click _Delete Forwarder_ to confirm.

Important:

* If you do **not** delete the cPanel account for which email is forwarded, **both** accounts will receive email.
* If you wish to forward all incoming mail from one account to another but do **not** want to receive email at the first account, create a forwarder from an address that does **not** have a cPanel account. If the account already exists, delete it.

### Add Forwarder

To add a mail forwarder, perform the following steps:

1. Click _Add Forwarder_.
2. In the _Address to Forward_ text box, enter the address for which you wish to forward incoming email.
3. Select the desired domain from the menu.
4. Select one of the following options:
   * _Forward to email address_ — Select this option to forward incoming email to another address. Enter the address to which you wish to forward email in the text box.
   * _Discard and send an error to the sender \(at SMTP time\)_ — Select this option to discard incoming email and automatically send a failure notice to the sender_._ Enter the desired failure message in the _Failure Message_ text box.
   * Click _Advanced Options_ to view the following additional options:
     * _Forward to a system account —_ Select this option to forward incoming email to a system user. Enter the desired username in the text box.

       Notes:

       * This text box accepts the username of any user on the server.
       * System accounts do **not** have a public-facing email address.

     * _Pipe to a program_ — To automatically forward incoming email to a program, enter a path to the program, relative to the account’s home directory \(for example, `utilities/support.pl`\) in the __text box. For more information, read the [Pipe to a Program](https://documentation.cpanel.net/display/68Docs/Forwarders#Forwarders-PipetoaProgram) section below.
     * _Discard \(Not Recommended\)_ — Select this option to discard incoming email without a failure notice.

       Important:We do **not** recommend this option, because the sender will **not** know that the delivery failed.
5. Click _Add Forwarder_.

### Pipe to a Program

{% hint style="info" %}
Important: Make **certain** that your script uses the proper file permissions \(`0700`\). To change your script’s file permissions, run the `chmod 0700 myscript.php` command, where `myscript.php` represents your script’s location and file name.
{% endhint %}

Use the _Pipe to a Program_ option to parse and enter email information into a different system. For example, use the _Pipe to a Program_ option to pipe email information to a program that enters email information into a ticket system.

* `STDIN` pipes email and headers to the program.
* Pipes can accept variables from the `$_SERVER` array and variables on the command line.
* The language or environment that you use may cause memory limit issues.
* If your script produces any output, even a blank line, the system will create a bounce message that contains that output.

When you use the _Pipe to a Program_ option, enter a path that is relative to your home directory. For example, to use the `/home/user/script.pl` script, enter `script.pl` in the _Pipe to a Program_ text box, where `user` represents your username.

## Domain forwarders

Domain forwarders send copies of all of a domain’s incoming email to another domain. Domain forwarders override the default address for the forwarded domain.

The _Forward All Email for a Domain_ table lists all of the domain forwarders for your account.

{% hint style="info" %}
Note: Domain forwarders only forward email when the system **cannot** deliver it to an address or autoresponder. For example, if a user sends an email to the `john@example1.com` address, the following actions might take place:

* If a `john@example1.com` address or autoresponder exists, cPanel will **not** forward the email.
* If a `john@example1.com` address or autoresponder does not exist, cPanel **will** forward the email.
{% endhint %}

### Add Domain Forwarder

To add a domain forwarder, perform the following steps:

1. Click _Add Domain Forwarder_.
2. Enter the domain to which you want to forward email.
3. Click _Add Domain Forwarder_.

### Delete a domain forwarder

To remove a domain forwarder, click _Delete_ next to the domain forwarder that you wish to remove, and then click _Delete Domain Forwarder_ to confirm.  


