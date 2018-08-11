# Managing subdomains in cPanel



A subdomain is a subsection of your website that can exist as a new website without a new domain name. Use subdomains to create memorable URLs for different content areas of your site. For example, you can create a subdomain for your blog that is accessible through **blog.example.com** and **www.example.com/blog**

_\(cPanel &gt;&gt; Home &gt;&gt; Domains &gt;&gt; Subdomains\)_

## Overview

This interface allows you to create and manage subdomains for your cPanel account. A subdomain is a subsection of your website that sometimes exists as a subdirectory of your `public_html` \(document root\) directory or your account’s home directory. Subdomains use a prefix in conjunction with the domain name.

For example, if the registered domain name is `example.com`, the subdomain will be `prefix.example.com`. You can use subdomains to create unique user accounts for “vanity domains.” This is helpful if, for example, you have a blog, or any other type of website that uses a domain specifically titled for a user.

Note:

Visitors **cannot** view your subdomain immediately. Changes to DNS records may require two days or more to reach all of the nameservers on the Internet.

## Create a subdomain

To create a subdomain, perform the following steps:

1. Enter the desired prefix in the _Subdomain_ text box.
2. Select the desired main domain from the menu.
3. Enter the home directory for the subdomain in the _Document Root_ text box.

   Note:

   This directory contains the files that pertain to the subdomain.

4. Click _Create_.

Warning:

Due to the order in which Apache processes its configuration file, wildcard subdomains may disrupt the functionality of proxy subdomains. We **strongly** recommend that you use wildcard subdomains only when absolutely necessary, or when you do not need to use proxy subdomains.

When you create an addon domain, parked domain, subdomain, or main domain, the system will attempt to automatically secure that domain with the best-available existing certificate. If no certificate exists, the system will generate a self-signed certificate to secure the new domain.

* If [AutoSSL](https://documentation.cpanel.net/display/68Docs/Manage+AutoSSL) is enabled for the account that owns the new domain, the system will add a request for an AutoSSL certificate to secure the new domain and install it when it becomes available.
* To open the subdomain’s main directory with the [_File Manager_](https://documentation.cpanel.net/display/68Docs/File+Manager) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Files &gt;&gt; File Manager\)_, click the link under _Document Root_ that corresponds to that subdomain.

## Search subdomains

To search existing subdomains, perform the following steps:

1. Enter the search criteria in the _Search_ text box.
2. Click _Go_.

## Modify a subdomain

### Modify the document root for a subdomain

To modify the document root for a subdomain, perform the following steps:

1. Click the notepad icon that corresponds to the subdomain that you want to manage.
2. Enter the new file path that you want to use as the document root in the available text text box.
3. Click _Change_.

### Enable or disable subdomain redirection

To enable or disable redirection of a subdomain, perform the following steps:

1. Click the _Manage Redirection_ link that corresponds to the subdomain that you wish to manage.
2. If you wish to redirect the subdomain, enter the link to which you want to redirect the subdomain in the available text text box.
3. Click _Save_.
4. To disable the redirect, click _Disable Redirection_.

### Remove a subdomain

To remove an existing subdomain, perform the following steps:

1. Click the _Remove_ link that corresponds to the subdomain that you want to remove.
2. Click _Yes_ to confirm that you want to remove the subdomain.
3. To keep the subdomain, click _No_.

