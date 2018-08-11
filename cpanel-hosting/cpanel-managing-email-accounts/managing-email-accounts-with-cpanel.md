# Managing email accounts with cPanel

Manage the email accounts associated with your domain. Use the _Set Up Mail Client_ interface to add an email account to your mobile device or desktop email client.

{% code-tabs %}
{% code-tabs-item title="Location Under cPanel" %}
```text
cPanel >> Home >> Email >> Email Accounts
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Overview

This interface allows you to add and manage email accounts for your domains.

## Add an email address

To add a new email address, perform the following steps:

1. Enter the email address that you wish to create in the _Email_ text box. If you manage more than one domain, make **certain** to select the appropriate domain from the menu.
2. Enter and confirm the new password in the appropriate text boxes.

   Notes:

   * The system evaluates the password that you enter on a scale of 100 points. `0` indicates a weak password, while `100` indicates a very secure password.
   * Some web hosts require a minimum password strength. A green password _Strength_ meter indicates that the password is equal to or greater than the required password strength.
   * Click _Password Generator_ to generate a strong password. For more information, read our [Password & Security](https://documentation.cpanel.net/display/68Docs/Password+and+Security) documentation.

3. Enter the quota in the _Mailbox Quota_ text box. The quota defines the amount of disk space the account may use to store email.

   Important:

   * Due to mail server constraints, you **cannot** assign quotas that exceed 4096000 MB \(4096 GB or 4 TB\).You **must** assign the _unlimited_ value for quotas that exceed this amount.
   * The system calculates mailbox quota use every four hours. For this reason, you may not receive notifications immediately if an email account reaches or exceeds its quota.

4. To send client configuration instructions to the account, select the _Send welcome email with mail client configuration instructions._ option.

   Note:

   The user can access this message via Webmail, or you can send the message to another mailbox with the _Email Instructions_ option in the [_Set Up Email Client_](https://documentation.cpanel.net/display/68Docs/Email+Accounts#EmailAccounts-SetUpEmailClient) interface.

5. Click _Create Account_. The system automatically sends an email to the newly-created email account with a link to the iPhone autoconfigure script.

### Change Password

Important:

Use a secure password. A secure password is **not** a dictionary word, and it contains uppercase and lowercase letters, numbers, and symbols.

To change a password, perform the following steps:

1. Click _Password_ for the appropriate email account.
2. Enter and confirm the new password in the appropriate text boxes.

   Notes:

   * The system evaluates the password that you enter on a scale of 100 points. `0` indicates a weak password, while `100` indicates a very secure password.
   * Some web hosts require a minimum password strength. A green password _Strength_ meter indicates that the password is equal to or greater than the required password strength.
   * Click _Password Generator_ to generate a strong password. For more information, read our [Password & Security](https://documentation.cpanel.net/display/68Docs/Password+and+Security) documentation.

3. Click _Change Password_ to store the new password.
   * If you do not wish to change the password, click _cancel_.

### Change Quota

The quota for an address defines the amount of mail, in Megabytes, that the account can store. When your mailbox exceeds this limit, the system returns any incoming mail to the sender with a message that states that the recipient’s mailbox is full. The system administrator can change this behavior in WHM’s __[_Exim Configuration Manager_](https://documentation.cpanel.net/display/68Docs/Exim+Configuration+Manager) __interface \(_WHM &gt;&gt; Home &gt;&gt; Service Configuration &gt;&gt; Exim Configuration Manager_\).

Notes:

* Make **certain** that you track your quota usage, because you **cannot** receive email with a full quota.
  * The quota calculation does **not** include your mailbox’s trash folder.
  * You **cannot** exceed the quota that your hosting provider sets.
  * Due to mail server constraints, you **cannot** assign quotas greater than 4096000 MB \(4096 GB or 4 TB\). You **must** assign the _unlimited_ value for quotas that exceed this amount_._
* The system calculates mailbox quota use every four hours. For this reason, you may not receive notifications immediately if an email account reaches or exceeds its quota. __

To change a mail quota, perform the following steps:

1. Click _Quota_.
2. Enter the new email quota, in Megabytes, in the appropriate text box. For an unlimited account, click _unlimited_.
3. Click _Change Quota_ to store the new value.
   * To retain the original quota, click _cancel_.

### Manage account suspension

Each row in the _Mail Account_ section of the interface displays two status icons.

The first status icon indicates whether the user can log in to, send mail from, and read their mail account. The second status icon indicates whether the mail account can receive incoming email.

| Icon | Status |
| :--- | :--- |
| ![](https://documentation.cpanel.net/download/attachments/2450081/incoming.png?version=1&modificationDate=1512102143879&api=v2) | Incoming email allowed. |
| ![](https://documentation.cpanel.net/download/attachments/2450081/no%20incoming.png?version=1&modificationDate=1512102143963&api=v2) | Incoming email suspended.If this is the only service suspended, then the user can still log in to, read, and send email. |
| ![](https://documentation.cpanel.net/download/attachments/2450081/login.png?version=1&modificationDate=1512102143925&api=v2) | Logins, reading, and sending allowed. |
| ![](https://documentation.cpanel.net/download/attachments/2450081/no%20login.png?version=1&modificationDate=1512102144007&api=v2) | Logins, reading, and sending suspended.If this is the only service suspended, the mailbox can still receive incoming email. |

To suspend logins, incoming email, or both for an email account, perform the following steps:

1. Click the appropriate _More_ link that corresponds to the email account to suspend.
2. Click the appropriate suspension link.
   * Click _Suspend_ to suspend both incoming mail and logins.
   * Click _Suspend Logins_ to suspend logins.
   * Click _Suspend Incoming_ to suspend incoming email.

To unsuspend logins, incoming email, or both for the email account, click _More_ and then click the apropriate _Suspend_ link.

{% hint style="info" %}
Note: When you suspend an email account, the system also suspends any aliases or forwarders that redirect email to the account.
{% endhint %}

### Delete

To delete an email address, perform the following steps:

1. Click _Delete_ for the account to remove.
2. Click _Delete_. To retain the email address, click _cancel_.

### Access Webmail

This feature allows you to access an email account with a web browser. To access this feature, perform the following steps:

1. Click _More_ for the appropriate email account.
2. Select _Access Webmail_.
3. Enter the password in the appropriate text box.
4. Click _Log in_.

For more information, read our [Webmail](https://documentation.cpanel.net/display/68Docs/Webmail) documentation.

### Set Up Email Client

This feature automatically configures your email client to access your cPanel email addresses. An email client allows you to access your email account from an application on your computer \(for example, Outlook® Express and Apple® Mail\).

To access this feature, click _More_ for the appropriate email account, and then select _Set Up Email Client_.

{% hint style="info" %}
**Notes:**

* An email client **must** already exist on your computer to automatically configure it with cPanel.
* To use an email client that the interface does not list, you **must** manually configure it. For more information on how to manually configure an email client, review your client’s documentation on the client’s website.
{% endhint %}

To configure your mail client, perform the following steps:

1. Select and download the appropriate configuration file from the list.
2. Run the script file to automatically configure your email client to use the selected address.

When the configuration process finishes, your email client opens automatically and logs in to your email account.

**Notes about email client configuration**

* If you installed a non-wildcard SSL certificate that matches your hostname, the name of your server matches your hostname. For example, if your hostname is `www.example.com` and your SSL certificate matches your hostname, your server’s name is `www.example.com`.
* If you installed a wildcard SSL certificate, the name of your server also matches any subdomains that correspond to the hostname’s domain. For example, an SSL certificate for `*.example.com` is valid for `my.example.com` and `foo.example.com`.
* If you did not install an SSL certificate, the server uses the mail subdomain of your domain. For example, `mail.example.com`. Also, if your certificate does not match your hostname, the server’s name is `mail.example.com`.

**Email Instructions**

To send a mail account’s client configuration instructions to a different email address, enter the address in the _Email Instructions_ text box and click _Send_.

### Email subaddresses

This feature, also known as plus addressing, allows senders to route a message directly to the folder of a mailbox.

Email subaddresses use the `username+folder@domain` format, where `username` represents the username of the mailbox and `folder` represents the folder’s name.

For example, if you send a message to `username+Important@example.com`, the mail server will route the message to the `Important` folder in the `username@example.com` mailbox.

Notes:

* If the folder does not already exist, the system will create that folder.
* You **must** subscribe to the folder in your email or webmail client for the folder to appear.

## Default email account

Your default email address appears under the _Default Email Account_ heading. The system creates this special email account when your hosting provider creates your cPanel account. The account’s username and password are identical to your cPanel account name and password.

* If your hosting provider configures this address to serve as a catch-all address for all mail that invalid usernames in your domain receive, it may receive a large amount of spam.
* You can check and delete the mail that this account receives. To do this through webmail, click _Access Webmail_ and select your desired webmail application.
* You can also use this account to send mail. To do this through webmail, click _Access Webmail_ and select your desired webmail application.

The actual address of the account is `account@example.com`, where `account` represents your account username. You **cannot** rename, delete, or place a quota on the default account. We recommend that you create a separate email account for daily use.

This address is also the default _From_ and _Reply-to_ address of outgoing email that your account’s PHP scripts send.

