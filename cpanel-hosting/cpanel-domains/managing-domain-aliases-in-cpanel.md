# Managing domain aliases in cPanel

Domain aliases make your website available from another domain name. For example, you can make **www.example.net** and **www.example.org** show content from **www.example.com**

{% code title="Location Under cPanel" %}
```text
cPanel > Home > Domains > Aliases
```
{% endcode %}

### Overview <a id="Aliases-Overview"></a>

Domain aliases are domains that you own, but which do not contain any content. Instead, they point to the contents of another domain or subdomain on your account. This is useful, for example, to hold a domain that you will later sell, or to redirect traffic to another domain.

Important:

Unless your hosting provider enables the _Allow Remote Domains_ option in the [_Tweak Settings_](https://documentation.cpanel.net/display/68Docs/Tweak+Settings) __interface \(_WHM &gt;&gt; Home &gt;&gt; Server Configuration &gt;&gt; Tweak Settings_\), you **must** perform the following actions **before** you attempt to create a domain alias:

* You **must** register the domain name with a valid registrar.
* You **must** point the domain to your account’s nameservers.

### Create a New Alias <a id="Aliases-CreateaNewAlias"></a>

To add a domain alias, enter the domain name in the text box and click _Add Domain_.

To open the alias domain’s home directory with the __[_File Manager_](https://documentation.cpanel.net/display/68Docs/File+Manager) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Files &gt;&gt; File Manager_\), click the link that corresponds to that alias under the _Domain Root_ column of the _Remove Aliases_ table.

When you create an addon domain, parked domain, subdomain, or main domain, the system will attempt to automatically secure that domain with the best-available existing certificate. If no certificate exists, the system will generate a self-signed certificate to secure the new domain.

If [AutoSSL](https://documentation.cpanel.net/display/68Docs/Manage+AutoSSL) is enabled for the account that owns the new domain, the system will add a request for an AutoSSL certificate to secure the new domain and install it when available.

Note:

You can create email accounts for domain aliases. For more information, read the [Alias domain email accounts](https://documentation.cpanel.net/display/68Docs/Aliases#Aliases-EmailAccounts) section below.

### Enable or disable domain alias redirection <a id="Aliases-Enableordisabledomainaliasredirection"></a>

To enable or disable redirection of a domain alias, perform the following steps:

1. Click _Manage Redirection_ for the domain alias that you wish to manage.
2. To redirect the domain, enter the link to which you wish to redirect the domain alias in the text box.
3. Click _Save_. To disable the redirection, click _Disable Redirection_.

### Remove Aliases <a id="Aliases-RemoveAliases"></a>

Notes:

* We **strongly** recommend that you create a full account backup before you perform this action.
* This action **only** removes the domain alias, its `vhost` entries, and its DNS entries. The system retains the alias’s directory contents.

To remove an existing domain alias, perform the following steps:

1. Click _Remove_ for the alias that you wish to remove.
2. Click _Yes_ to confirm that you wish to remove the domain alias. To retain the domain alias, click _No_.

### Search aliases <a id="Aliases-Searchaliases"></a>

To search through the list of domain aliases, enter the search criteria in the _Search_ text box and click _Go_. Results that match your search criteria will populate the table.

### Domain alias email accounts <a id="Aliases-EmailAccountsDomainaliasemailaccounts"></a>

To add new email accounts, use cPanel’s [_Email Accounts_](https://documentation.cpanel.net/display/68Docs/Email+Accounts) interface \(_cPanel &gt;&gt; Home &gt;&gt; Email &gt;&gt; Email Accounts_\), or run the `/scripts/addpop` script from the command line.

* To move **one** email account under a domain, run the following command:

  | `mv` `/home/old_account/mail/domain_name/email_account` `/home/new_account/mail/domain_name/` |
  | :--- |


  When you run this command, the system creates the `/home/new_account/mail/domain_name/` directory.

* To move **all** of the email accounts under a domain, run the following command:

  | `mv` `/home/old_account/mail/domain_name` `/home/new_account/mail` |
  | :--- |

* After you move the files, change the new account’s ownership with the following command:

  | `chown` `-R new_account:new_account /home/new_account/mail/domain_name` |
  | :--- |


  Note:

  Make certain that you verify ownership of the email account after you move it.

If you remove the domain alias, its email accounts will no longer appear in the [_Email Accounts_](https://documentation.cpanel.net/display/68Docs/Email+Accounts) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Email &gt;&gt; Email Accounts_\). However, the email accounts’ contents still exist in the mail folder of the user’s `home/username/mail/` directory.

* If you add the domain again, to the same account as the primary domain, an addon domain, or an alias, the email accounts reappear in the interface.
* If you change the account’s primary domain name to the un-aliased domain name, the email accounts reappear in the interface.
  * You or your hosting provider can perform this action in WHM’s [_Modify an Account_](https://documentation.cpanel.net/display/68Docs/Modify+an+Account) __interface \(_WHM &gt;&gt; Home &gt;&gt; Account Functions &gt;&gt; Modify an Account\)_.
  * When you perform this action, the former primary domain name’s mailboxes will **not** appear in the [_Email Accounts_](https://documentation.cpanel.net/display/68Docs/Email+Accounts) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Email &gt;&gt; Email Accounts_\). However, the files will still exist.
* If you move the domain to a different account, you **must** add the email accounts manually **and** move the contents of the email accounts manually.

  Note:

  The email accounts **must** follow the same name and domain formats that they previously followed.

### Addon vs. alias domains <a id="Aliases-Addonvs.aliasdomains"></a>

| Characteristic | Addon domains | Alias domains |
| :--- | :--- | :--- |
| The main domain appears in the address bar. | Yes | No |
| The domain uses the following Apache directive: | VirtualHost | ServerAlias |
| The domain uses separate logs. | Yes | No |
| The domain uses separate stats. | Yes | No |
| The system treats the domain as a subdomain \(other than the URL\). | Yes | No |
| This type of domain is ideal for multiple domains that share the same address. | No | Yes |

