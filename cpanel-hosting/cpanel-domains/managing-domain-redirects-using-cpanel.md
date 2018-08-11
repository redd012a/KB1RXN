# Managing domain redirects using cPanel

A redirect allows you to make one domain redirect to another domain, either for a website or a specific web page. For example, create a redirect so that **www.example.com** automatically redirects users to **www.example.net**.

```text
cPanel > Home > Domains > Redirects
```

## Overview

The _Redirects_ interface allows you to send all of the visitors of a domain or particular page to a different URL.

For example, if create a page with a long URL, use the _Redirects_ interface to add a redirect from a short URL to the long URL. Visitors can enter the short URL to access the content of the long URL.

Warning:

This feature will **not** function if your System Administrator enabled [ModSecurity](https://documentation.cpanel.net/display/68Docs/ModSecurity+Tools)™.

## Add a redirect

To add a redirect, perform the following actions:

1. Select a redirect type from the _Type_ menu.
   * _Permanent \(301\) —_ This __option notifies the visitor’s browser to update its records.
   * _Temporary \(302\)_ — This option does **not** update the visitor’s bookmarks.
2. Select a domain name from the menu, or select \* \*_All Public Domains\* \*_ to redirect all of the domains that your cPanel account controls.
3. In the text box to the right of the domain selection menu, enter the rest of the URL from which you wish for the server to redirect visitors. For example, if you wish to redirect `http://example.com/directory.file.html` to another URL, enter `directory/file.html` in this text box.
4. In the _redirects to_ text box, enter the URL to which you wish to redirect users.

   Important:

   You **must** specify a protocol in this text box. For example, `http://`, `https://`, or `ftp://`.

5. Select one of the following options:
   * _Only redirect with www_. — This option only redirects visitors who enter the `www.` prefix before the domain name part of the URL.
   * _Redirect with or without www._ — This option redirects all users, regardless of whether the visitor enters the `www.` prefix before the domain name part of the URL.
   * _Do Not Redirect www._ — This option does **not** redirect users who enter the `www.` prefix before the the domain name part of the URL.
6. Select the _Wildcard Redirect_ option if you wish to redirect all files within a directory to the same filename in the new directory.
   * For example, if you enable the _Wild Card Redirect_ option and `example1.com` redirects to `example.com`, then a visitor who tries to access the `http://example1.com/pic.jpg` URL redirects to the `http://example.com/pic.jpg` URL.
7. Click _Add_.
   * To test the redirect, click the link under _Directory_ in the _Current Redirects_ table. If you properly configured the redirect, the system directs you to the original domain.

Important:

If you use a third-party application or content management system to add a redirect, such as WordPress®, the redirect may not function properly. When you add a redirect with cPanel interface, the system places redirect rules at the bottom of the `.htaccess` file. Some third-party applications ignore the rule that you add, because those applications only read rules and configurations that their section of the `.htaccess` file contains.

The following example displays the configuration that you **must** add to the **top** of the `.htaccess` file to add a redirect for the [Drupal](https://www.drupal.org/) content management system.

In the following example:

* `drupal.user.example.com` represents the URL to redirect.
* `http://cpanel.net/` represents the URL to which to redirect.

  | 12345678 | `<IfModule mod_rewrite.c>RewriteEngine onRewriteBase /RewriteRule ^index\.php$ - [L]RewriteCond %{HTTP_HOST} ^drupal\.user\.example\.com$ [OR]RewriteCond %{HTTP_HOST} ^www\.drupal\.user\.example\.com$RewriteRule ^cptest$ "http\:\/\/cpanel\.net\/" [R=301,L]</IfModule>` |
  | :--- | :--- |

Note:

You **cannot** edit a redirect. To modify a redirect, you **must** delete it, and then recreate it.

## Remove a redirect

To remove a redirect, perform the following steps:

1. Click _Delete_ next to the redirect that you wish to remove.
2. Click _Yes_.

## Search your redirects

To search your redirects, perform the following steps:

1. Enter the search criteria in the _Search_ text box.
2. Click _Go_.

The interface will list the redirects that match your search criteria.

To sort your list of redirects, click the appropriate table heading.

