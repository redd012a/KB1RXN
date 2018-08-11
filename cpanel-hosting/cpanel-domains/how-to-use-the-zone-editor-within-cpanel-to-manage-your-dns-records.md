# How to use the Zone Editor within cPanel to manage your DNS records

DNS converts domain names into computer-readable IP addresses. DNS zone files configure domain names to the correct IP addresses. This feature allows you to create and edit these zone files.

```text
cPanel >> Home >> Domains >> Zone Editor
```

## Overview

DNS \(Domain Name Service\) converts human-readable domain names \(for example, `example.com`\) to computer-readable IP addresses \(for example, `192.0.32.10`\). DNS uses zone files that reside on your server to map domain names to IP addresses.

Several different types of records reside in a domain’s zone file. This feature allows you to create, edit, and delete the following records:

* A 
* AAAA
* CAA \(Certificate Authority Authorization Record\)
* CNAME \(Canonical Name Record\)
* DMARC \(Domain-based Message Authentication, Reporting, and Conformance\)
* MX \(Mail Exchanger\)
* SRV \(Service Record\)
* TXT \(Text Record\)

Note:

To access all available zone record types, your systems administrator **must** enable the _Advanced Zone Editor_ feature in WHM’s __[_Feature Manager_](https://documentation.cpanel.net/display/68Docs/Feature+Manager) __interface \(_WHM &gt;&gt; Home &gt;&gt; Packages &gt;&gt; Feature Manager_\).

## Domains

This interface displays your account’s domains. For each domain in the list, you can perform some actions directly. Click the text to perform that action.

| Text | Action |
| :--- | :--- |
| _A Record_ | Add an A record for this domain. |
| _CNAME Record_ | Add a CNAME record for this domain. |
| _MX Record_ | Add an MX record for this domain. |
| _DNSSEC Record_ | Enable or disable DNSSEC for this domain. |
| _Manage_ | Add or edit additional records for this domain. |

To refresh the list of domains, click the gear icon \(![](https://documentation.cpanel.net/download/attachments/1794660/Gear.png?version=3&modificationDate=1515448151574&api=v2)\) and select _Refresh List._

## Manage Zone

This interface displays the zone records for the selected domain. To filter the list of zone records, enter a name in the text box, or select one of the record type filters.

## Add a record

To add a record, perform the following steps:

1. If this account owns more than one domain, click _Manage_ next to the domain that you wish to modify.
2. Click the arrow next to _Add Record_ to select a record type:
   * _Add A Record — ****_ This record maps hostnames to IP addresses. A records allow DNS servers to identify and locate your website and its various services on the Internet. Without appropriate A records, your visitors cannot access your website, FTP site, or email accounts.

     Note:

     cPanel configures your DNS records so that visitors can resolve your website and its services, such as FTP and email. **Only** add A records when you add a service that cPanel & WHM or your service provider does not provide.

   * _Add AAAA Record_ — This record maps hostnames to IPv6 addresses.
   * _Add CAA Record_ — This record allows you to specify which certificate authority \(CA\) will issue an SSL certificate for a domain. Click to view the CAA parameters

     Note:

     If no CAA records exist for a domain, all CAs can issue certificates for that domain. If conflicting CAA records already exist, remove the existing CAA records or add one for the desired CA. For example, a CAA record for Comodo would resemble the following example, where `example.com` represents the domain name:

     | `example.com. 86400 IN CAA 0 issue "comodoca.com"` |
     | :--- |


     For more information about a CA’s requirements, read their documentation.

   * _Add CNAME Record_ — This record creates an alias for another domain name, which DNS looks up. This is useful, for example, if you point multiple CNAME records to a single A record in order to simplify DNS maintenance.

     Note:

     You **cannot** point a CNAME record to an IP address.

   * _Add DMARC Record_ — This record allows you to validate an email message’s sender and filter spam email messages on your domain. If you select this option, the system creates a [TXT record](https://documentation.cpanel.net/display/68Docs/Zone+Editor#ZoneEditor-txtrecord) with a default DMARC record. The system also displays a form that allows you to specify the domain’s DMARC policy \(_None, Quarantine,_ or _Reject_\), as well as the following optional parameters: Click to view the DMARC parameters
3. * _Add MX Record —_  This record allows you to route a domain’s incoming mail to a specific server. Changes that you make to a domain’s MX \(Mail Exchanger\) control where the system delivers email for a domain.
   * _Add SRV Record_ — This record provides information about available services on specific ports on your server.

     Note:

     The SRV record **must** point at a hostname with an A \(or AAAA\) record. You **cannot** point an SRV record at a CNAME record.

   * _Add TXT Record —_ This record contains text information for various services to read. For example, TXT records can specify data for the SPF, DKIM, or DMARC email authentication systems.  
     Click the links below to view examples of each TXT record:

     Note:

     The TXT record text box accepts invalid data and does **not** issue a warning. SPF Records DKIM Records DMARC Records  
     __

     Note:

     On servers that run CentOS 7, you may see a `named` warning about the absence of SPF resource records on DNS.

     * This warning is **not** relevant on CentOS 7 servers, because [RFC 7208 deprecated SPF records](https://tools.ietf.org/html/rfc7208). CentOS 7 servers use TXT records instead of SPF records.
     * Red Hat 7.1 and CentOS 7.1 both contain `bind-9.9.4-23.el7`, which is an updated version of BIND that complies with RFC 7208. To resolve this issue, update your operating system to a version that contains the updated version of BIND. For more information, read the [the Red Hat Bugzilla case about SPF record errors](https://bugzilla.redhat.com/show_bug.cgi?id=1215164).
4. Enter the appropriate information for the record type that you selected.
5. Click _Add Record_.

## Edit a record

To edit a record, perform the following steps:

1. If this account owns more than one domain, click _Manage_ next to the domain you want to modify.
2. Click _Edit_ next to the record that you wish to edit.
3. Change the information in the text boxes as necessary.
4. Click _Edit Record_ to save your changes, or click _Cancel_ to discard them.

## Delete a record

To delete a record, perform the following steps:

1. If this account owns more than one domain, click _Manage_ next to the domain you want to modify.
2. Click _Delete_ next to the record that you wish to remove.
3. Click  _Delete_ i n the confirmation dialog box _._

## Reset zone files

Warning:

This feature erases **any** modifications that you made to your zone records. The system attempts to save the domain’s TXT entries. We recommend that you record any changes that you wish to save before you use this feature.

To reset your DNS zone files to the defaults that your hosting provider specifies, perform the following steps:

1. If this account owns more than one domain, click _Manage_ next to the domain that you wish to reset.
2. Click the gear icon \(![](https://documentation.cpanel.net/download/attachments/1794660/Gear.png?version=3&modificationDate=1515448151574&api=v2)\) and select _Reset Zone_.
3. Read the warning about the consequences.
4. Click _Continue_ to reset your zone, or _Cancel_ to return to the _Manage Zone_ interface.

## DNSSEC

Important:

This feature **only** appears if your system administrator disables DNS clustering **and** installs PowerDNS in either of the following interfaces:

* WHM’s __[_Initial Setup Assistant_](https://documentation.cpanel.net/display/68Docs/Initial+Setup+Assistant) __.
* WHM’s __[_Nameserver Selection_](https://documentation.cpanel.net/display/68Docs/Nameserver+Selection) __interface \(_WHM &gt;&gt; Home &gt;&gt; Service Configuration &gt;&gt; Nameserver Selection_\).

DNS Security Extensions \(DNSSEC\) add a layer of security to your domains’ DNS records. DNSSEC uses digital signatures and cryptographic keys to validate that DNS responses are authentic. These digital signatures protect clients from various forms of attack, such as Spoofing or a Man-in-the-Middle attack.

Important:

* DNSSEC keys remain on a server after you terminate an account. If you restore an account on the same server from which you deleted it, the account’s DNSSEC keys remain valid.
* If you transfer the account to another server, you **must** reconfigure DNSSEC for the domains and update the domain server records on the registrar. The system does **not** include DNSSEC keys in an account’s backup file.

 Click here for transfer instructions

### Enable DNSSEC

To enable DNSSEC for a domain, perform the following steps:

1. If this account owns more than one domain, click _DNSSEC_ next to the domain you want to modify.
2. Click _Enable._ The system will generate a new DNSSEC key, and a new line will appear that contains the following information:

   | Column | Description |
   | :--- | :--- |
   | _Key Tag_ | An integer value that identifies the domain’s DNSSEC record. |
   | _Algorithm_ | The record’s encrypted signature. |
   | _Digest Type_ | The algorithm type that constructs the digest. Select the digest type that your registrar supports. |
   | _Digest_ | An alpha-numeric string that the algorithm generates. |

Important:

After you generate the domain’s DNSSEC key, you **must** configure a Domain Server \(DS\) record with your domain registrar. Click the links below for DS record instructions with some of the most popular domain registrars. GoDaddy Namecheap OpenSRS

### Disable DNSSEC

To disable DNSSEC for a domain, perform the following steps:

1. If this account owns more than one domain, click _DNSSEC_ next to the domain you want to modify.
2. Click _Disable._

Important:

After you disable DNSSEC, you **must** delete the DS record with your domain registrar. Click the links below for DS record instructions with some of the most popular domain registrars. GoDaddy Namecheap OpenSRS  


