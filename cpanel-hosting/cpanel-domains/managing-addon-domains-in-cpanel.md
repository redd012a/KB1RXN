# Managing addon domains in cPanel

An addon domain is an additional domain that the system stores as a subdomain of your main site. Use addon domains to host additional domains on your account.

{% code title="Location under cPanel" %}
```text
cPanel > Home > Domains > Addon Domains
```
{% endcode %}

## Overview

Addon domains allow you to control multiple domains from a single account. An addon domain links a new domain name to a directory in your account, and then stores its files in that directory.

Important:

Your hosting provider **must** specify a maximum number of addon domains that you can create \(greater than `0`\) in the [_Modify an Account_](https://documentation.cpanel.net/display/68Docs/Modify+an+Account) interface \(_WHM_ &gt;&gt; _Home &gt;&gt; Account Functions &gt;&gt; Modify an Account_\). A value of `0` **prevents** addon domain creation.

## Create an addon domain

To create an addon domain, perform the following steps:

1. Enter the new addon domain’s name in the _New Domain Name_ text box. When you enter the domain name, cPanel automatically populates the _Subdomain_ and _Document Root_ text boxes.
2. To create multiple addon domains with the same username and different extensions \(for example, `example.com` and `example.net` \), manually enter a unique username in the _Subdomain_ text box.
3. To choose a document root other than the automatically populated value, manually enter the directory name in the _Document Root_ text box.
4. To create an FTP account for the new addon domain, select the _Create an FTP account associated with this Addon Domain_ checkbox. If you select this checkbox, additional settings will appear:
   * cPanel automatically populates the _FTP Username_ text box. To select a different FTP account username, manually enter the desired username.
   * Enter and confirm the new password in the appropriate text boxes.

     Notes:

     * The system evaluates the password that you enter on a scale of 100 points. `0` indicates a weak password, while `100` indicates a very secure password.
     * Some web hosts require a minimum password strength. A green password _Strength_ meter indicates that the password is equal to or greater than the required password strength.
     * Click _Password Generator_ to generate a strong password. For more information, read our [Password & Security](https://documentation.cpanel.net/display/68Docs/Password+and+Security) documentation.
5. Click _Add Domain_.

To add files to the addon domain’s home directory, click [_File Manager_](https://documentation.cpanel.net/display/68Docs/File+Manager).

When you create an addon domain in the cPanel interface, the system **automatically** creates a subdomain. To alter or delete the subdomain after you create it, you may alter or delete the information that the addon domain’s website displays.

Also, when you create an addon domain, parked domain, subdomain, or main domain, the system will attempt to automatically secure that domain with the best-available existing certificate. If no certificate exists, the system will generate a self-signed certificate to secure the new domain.

If [AutoSSL](https://documentation.cpanel.net/display/68Docs/Manage+AutoSSL) is enabled for the account that owns the new domain, the system will add a request for an AutoSSL certificate to secure the new domain and install it when it becomes available.

Note:

The system stores and displays the addon domain’s traffic statistics as part of the subdomain’s traffic statistics.

## Modify Addon Domain

### Modify the document root for an addon domain

To modify the document root for an addon domain, perform the following steps:

1. Click the edit icon \(![](https://documentation.cpanel.net/download/thumbnails/1794058/edit_icon.png?version=3&modificationDate=1515180306406&api=v2)\) for the addon domain that you wish to manage under the _Document Root_ column.
2. Enter the new file path to the addon domain’s document root in the available text box.
3. Click _Change_.

### Enable or disable addon domain redirection

To disable or enable redirection of an addon domain, perform the following steps:

1. Click _Manage Redirection_ for the addon domain that you wish to manage.
2. To redirect the domain, enter the link to which you wish to redirect the addon domain.
3. Click _Save_, or, to disable the redirection, click _Disable Redirection_.

### Remove an addon domain

To remove an addon domain, perform the following steps:

1. Click _Remove_ for the addon domain that you wish to remove.
2. Click _Yes_.

## Email accounts in addon domains

Note:

In the following examples:

* `old_account` represents the cPanel account **from** which you wish to move the addon domain’s email account or accounts.
* `new_account` represents the cPanel account **to** which you wish to move the addon domain’s email account or accounts.
* `domain_name` represents the addon domain’s name.
* `email_account` represents the name of the addon domain’s email account that you wish to move.

You can create email accounts for addon domains. To learn how to set up an email account for an addon domain, read our [Email Accounts](https://documentation.cpanel.net/display/68Docs/Email+Accounts) documentation.

When you remove the addon domain, its email accounts will no longer appear in the cPanel interface. However, the contents for this email account still exist in the `home/username/mail` directory.

* If you add the domain back to the same account as the primary domain, an addon domain, or a parked domain, the email accounts reappear in the cPanel interface.
* If you move the domain to a different account, you **must** add the email accounts manually and move the contents of the email account manually. The email accounts **must** follow the same name and domain format that they previously followed.
  * Use the _Email Accounts_ interface to add new accounts, or run the `/scripts/addpop` script to manually add new email accounts.
  * To move **one** email account under a domain, you can run the following command:

    |  `mv` `/home/old_account/mail/domain_name/email_account` `/home/new_account/mail/domain_name/` |
    | :--- |


    After you run this command, the system creates the `/home/new_account/mail/domain_name/` directory.

  * To move **all** the email accounts under a domain, run the following command:

    | `mv /home/old_account/mail/domain_name /home/new_account/mail` |
    | :--- |


    After you move the files, run the following command to change the ownership of the new account:

    | `chown` `-R new_account:new_account /home/new_account/mail/domain_name.` |
    | :--- |

Note:

Verify ownership of the email account after you move it.

## Search addon domains

To search the list of addon domains, perform the following steps:

1. Enter the search criteria into the _Search_ box.
2. Click _Go_.

The interface lists results that match your search criteria.

## Addon and alias domains

| Characteristic | Addon domains | Alias domains |
| :--- | :--- | :--- |
| The main domain appears in the address bar. | Yes | No |
| The domain uses the following Apache directive: | VirtualHost | ServerAlias |
| The domain uses separate logs. | Yes | No |
| The domain uses separate stats. | Yes | No |
| The system treats the domain as a subdomain \(other than the URL\). | Yes | No |
| This type of domain is ideal for multiple domains that share the same address. | No | Yes |

