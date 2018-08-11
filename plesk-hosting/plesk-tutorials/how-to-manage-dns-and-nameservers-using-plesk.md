# How to manage DNS and nameservers using Plesk

## Managing DNS Records

A domain name is a human-readable Internet address of a website that can be used to reach the website. The translation of human-readable names into machine-readable ones is carried out by the Domain Name System, or DNS for short. It is very important for the DNS settings for your websites to be correct, otherwise the operation of your services may be disrupted. For example, your domain may become unavailable, or mail may fail to reach your mail server. Plesk can function as the primary \(master\) or a secondary \(slave\) name server for your domains. DNS settings are configured automatically, but can be changed from the interface. If the DNS service for your domains is provided by third-party name servers, you can disable the DNS service in Plesk.

### Adding and Modifying DNS Records

**Note:** This section is meant for advanced users. Configuring DNS settings incorrectly can negatively affect website and mail accessibility.

For each new domain name, Plesk automatically creates a DNS zone in accordance with the settings configured by your service provider. The domain names should work fine with the automatic configuration. However, if you use Plesk NS server and need to perform custom modifications in the domain name zone, you can do that in your control panel.

To view the resource records in a DNS zone of a domain, go to **Websites & Domains** &gt; **DNS Settings**.

![DNS\_settings](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77086.png)

To add a resource record to the zone, go to **Websites & Domains** &gt; **DNS Settings** &gt; **Add Record**.

![Add\_DNS\_record](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77088.png)

To modify the properties of a resource record, go to **Websites & Domains** &gt; **DNS Settings** and click on the record.

In addition to the resource records described above, there is also a Start of Authority record. This record indicates that this DNS name server is responsible for the domain’s DNS zone. It also contains settings that affect propagation of information about the DNS zone in the Domain Name System.

### Using External Name Servers

If you host websites on your account and do not want to use Plesk as your primary \(master\) NS server, you have the following options:

* Use Plesk name server as a secondary \(slave\) name server. Choose this option if you have a standalone name server acting as a primary \(master\) name server for your websites.
* Disable DNS for your domain in Plesk. Choose this option if you have external primary and secondary name servers that are authoritative for your websites.

To switch the Plesk DNS server to a secondary name server, go to **Websites & Domains** &gt; **DNS Settings** and click **Master/Slave**.

To revert the Plesk DNS server to the primary name server, go to **Websites & Domains** &gt; **DNS Settings** and click **Master/Slave**.

To switch off Plesk’s DNS service for a site served by external name servers, go to **Websites & Domains** &gt; **DNS Settings** and click **Disable**.  


