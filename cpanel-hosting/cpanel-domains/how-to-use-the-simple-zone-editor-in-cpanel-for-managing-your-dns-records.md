# How to use the Simple Zone Editor in cPanel for managing your DNS Records

DNS converts domain names into computer-readable IP addresses. DNS zone files configure domain names to the correct IP addresses. This feature allows you to create and edit these zone files using a simplified interface.

{% hint style="warning" %}
**Warning:** This interface is deprecated and will be removed in a future release. Use the new [Zone Editor](https://alfa.cloudns.io:2083/cpsess1488551919/frontend/paper_lantern/zone_editor/index.html) to perform the same functions.
{% endhint %}

{% code title="Location under cPanel" %}
```text
cPanel > Home > Domains > Simple Zone Editor
```
{% endcode %}

## Overview

Important:

We deprecated this interface in cPanel & WHM version 62. We **strongly** recommend that you use cPanel’s [_Zone Editor_](https://documentation.cpanel.net/display/68Docs/Zone+Editor) interface \(_cPanel &gt;&gt; Home &gt;&gt; Domains &gt;&gt; Zone Editor_\).

DNS \(Domain Name System\) is the component of the Internet that converts human-readable domain names \(for example, `example.com`\) into computer-readable IP addresses \(for example, `192.0.32.10`\). DNS uses zone files that reside on your server to map domain names to IP addresses.

There are several different types of records in a domain’s zone file. This interface allows you to create and delete A and CNAME \(Canonical Name\) records.

Note:

You **cannot** set a record’s time to live \(TTL\) in this interface. Records that you create with this interface default to the TTL that your hosting provider specifies. To set the TTL for a record, use cPanel’s [_Advanced Zone Editor_](https://documentation.cpanel.net/display/68Docs/Advanced+Zone+Editor) __interface _\(cPanel &gt;&gt; Home &gt;&gt; Domains &gt;&gt; Advanced Zone Editor\)_.

## Add an A record

An **A record** is a DNS record that maps hostnames to IP addresses. A records are essential because they allow DNS servers to identify and locate your website and its various services on the Internet. Without appropriate A records, your visitors cannot access your website, FTP site, or email accounts.

To add an A record, perform the following steps:

1. If this account owns more than one domain, select the domain that you wish to manage from the _Domain_ menu.
2. Enter the _Name_ and _Address_ of the A record.
3. Click _Add A Record_.

Warning:

cPanel & WHM configures your DNS records so that visitors can resolve your website and its services \(for example, FTP and Email\). **Only** add A records when you add a service that cPanel & WHM or your service provider do not provide.

## Add a CNAME record

A **CNAME** **record** creates an alias for another domain name, which DNS looks up. This is useful, for example, if you point multiple CNAME records to a single A record in order to simplify DNS maintenance.

To add a CNAME record, perform the following steps:

1. If this account owns more than one domain, select the domain that you wish to manage from the _Domain_ menu.
2. Enter CNAME record in the _Name_ and _CNAME_ text box.
3. Click _Add CNAME Record_.

## Delete a record

To delete an A or CNAME record, perform the following steps:

1. If this account owns more than one domain, select the domain that you wish to manage from the _Domain_ menu.
2. Click the _Delete_ link next to the record that you wish to remove.
3. Click _Delete_.

## DNSSEC

Important:

This feature **only** appears if your System Administrator installs PowerDNS in either of the following interfaces:

* WHM’s __[_Initial Setup Assistant_](https://documentation.cpanel.net/display/68Docs/Initial+Setup+Assistant).
* WHM’s __[_Nameserver Selection_](https://documentation.cpanel.net/display/68Docs/Nameserver+Selection) __interface \(_WHM &gt;&gt; Home &gt;&gt; Service Configuration &gt;&gt; Nameserver Selection_\).

DNS Security Extensions \(DNSSEC\) add a layer of security to your domains’ DNS records. DNSSEC uses digital signatures and cryptographic keys to validate that DNS responses are authentic. These digital signatures protect clients from various forms of attack, such as Spoofing or a Man-in-the-Middle attack.

Important:

* DNSSEC keys remain on a server after you terminate an account. If you restore an account on the same server from which you deleted it, the account’s DNSSEC keys remain valid.
* If you transfer the account to another server, you **must** reconfigure DNSSEC for the domains and update the domain server records on the registrar. The system does not include DNSSEC keys in an account’s backup file.  
  To transfer an account with DNSSEC enabled domains, perform the following steps for each domain:

  1. Remove the Domain Server \(DS\) records from the registrar.
  2. Wait for the changes to propagate \(up to 72 hours\).
  3. Disable DNSSEC on the domain \(optional\).
  4. Transfer the account to the new server.
  5. Enable DNSSEC on the new server.

  If you do not remove the old DS records from the registrar, the domains may produce DNS resolution issues due to invalid DNSSEC responses.

### Enable DNSSEC

To enable DNSSEC for a domain, perform the following steps:

1. If this account owns more than one domain, select the domain that you wish to manage from the _Domain_ menu.
2. Click _Enable._ The system will generate a new DNSSEC key, and a new line will appear that contains the following information:

   | Column | Description |
   | :--- | :--- |
   | _Key Tag_ | An integer value that identifies the domain’s DNSSEC record. |
   | _Algorithm_ | The record’s encrypted signature. |
   | _Digest Type_ | The algorithm type that constructs the digest. Select the Digest Type that your registrar supports. |
   | _Digest_ | An alpha-numeric string that the algorithm generates. |

Important:

After you generate the domain’s DNSSEC key, you **must** configure a Domain Server \(DS\) record with your domain registrar. Click the links below for DS record instructions with some of the most popular domain registrars. GoDaddy Namecheap OpenSRS

### Disable DNSSEC

To disable DNSSEC for a domain, perform the following steps:

1. If this account owns more than one domain, select the domain that you wish to manage from the _Domain_ menu.
2. Click _Disable._

Important:

After you generate the domain’s DNSSEC key, you **must** delete the DS record with your domain registrar. Click the links below for DS record instructions with some of the most popular domain registrars. GoDaddy Namecheap OpenSRS  


