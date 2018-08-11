# Managing MySQL databases remotely using ‘Remote MySQL’ in cPanel



## Overview

This feature allows remote hosts \(servers\) to access MySQL® databases on your account. This is useful, for example, if you wish to allow shopping cart or guestbook applications on other servers to access your databases.

Warning:

Your hosting provider may add remote hosts to this list at the server level. If you see a hostname that you do not recognize or remove a hostname that reappears later, contact your hosting provider.

## Allow a remote server to access your databases

To specify remote hosts that can access MySQL databases on your account, perform the following steps:

1. Enter the host’s name or IP address in the _Host_ text box.

   Notes:

   * You may enter a fully qualified domain name \(FQDN\) or an IP address.
   * You may use the percentage sign character \(`%)` as a wildcard. For example, to allow access from all IP addresses that begin with `192.68.0`, enter `192.68.0.%`.

2. Click _Add Host_.

## Deny a remote server access to your databases

To deny database access to a remote host, perform the following steps:

1. Click _Delete_ next to the host’s name or IP address.
2. Click _Yes_.

