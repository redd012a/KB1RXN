# Managing email routing with cPanel

## Overview

This interface allows you to configure how the system routes a domain’s incoming mail.

For example, you can use this interface to configure the server as a backup mail exchanger, which will hold a domain’s mail until the primary mail exchanger is available. 

## Configure Email Routing

{% hint style="warning" %}
**Warning:** Misconfigured _Email Routing_ settings can disrupt your ability to receive mail. If you are unsure which option to choose, contact your system administrator or hosting provider.
{% endhint %}

To configure how your server routes mail for a domain, perform the following steps:

1. Select the desired domain from the menu. If only one domain exists on your cPanel account, the system selects it automatically.
2. Select one of the following options under _Configure_ _Email Routing_:
   * _Automatically Detect Configuration_ —    The system uses the following criteria to configure the email routing settings:

     * _Local Mail Exchanger_  — The lowest numbered mail exchanger points to an IP address on this server.
     * _Backup Mail Exchanger_  — The lowest numbered mail exchanger points to an IP address not on this server.
     * _Remote Mail Exchanger_  — No mail exchangers point to an IP address on this server.

     Note:

     If the configured Mail Exchange \(MX\) records do not resolve, automatic detection will **not** occur.

   * _Local Mail Exchanger_ — The server always accepts mail for this domain. The system will deliver mail to the local mailbox.

     Note:

     Choose this option if your server uses smart hosts or another gateway service to filter mail.

   * _Backup Mail Exchanger_ — The server functions as a backup mail exchanger. The system will hold mail for this domain until a lower number mail exchanger becomes available .

     Note:

     You **must** configure the primary MX record to point to the appropriate exchanger.

   * _Remote Mail Exchanger_ — The server will **not** accept mail for this domain. The system sends all mail for this domain to the lowest numbered mail exchanger.

     Note:

     You **must** configure the primary MX record to point to the appropriate exchanger.
3. Click _Change_.

