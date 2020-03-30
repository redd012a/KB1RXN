# Improving mail deliverability \(SPF & DKIM\)

 **cPanel &gt;&gt; Email - Authentication**  
  
The following video guide walks you through improving email deliverability from your Smart account. It includes using [mail-tester.com](http://www.mail-tester.com/) to check SPF and DKIM records and how to set them correctly in your cPanel/DNS.

{% embed url="https://youtu.be/WlU6rpqOPes" caption="Improving Mail Deliverability \(SPF & DKIM\)" %}

## cPanel Email Deliverability Tool – SPF and DKIM Records

As you may know, if mail service is unauthenticated you can face the following issues:  


* emails you send are delivered to Spam/Junk folders 
* emails you send bounce with "SPF record failure" error
* your Inbox gets numerous "Failed delivery" bounce backs of the emails you never sent

In the first case, recipient mail server looks up SPF record for your domain, and if it is not added / does not match actual outgoing server IP address, such a mail delivery will fail. Such checking mechanism is implemented in order to make sure email comes from a legitimate sender and verified sender.  
  
Second situation takes place when there is no SPF/DKIM configured for your domain or they are configured incorrectly, which lets unauthorized party to forge emails using @yourdomain.com mailbox. Such cases are called **mail spoofing**.  
  
**Email Deliverability** is an effective set of anti-spoofing and anti-spamming tools available in cPanel.  
  
The **Email Deliverability** table displays your cPanel account's domains and allows you to address any existing problems with your mail-related DNS records – **SPF and DKIM**.  
  


* **SPF record**

Nowadays the vast majority of spam emails have fake data in the «From» field. Spammers and fraudsters use special tools to send their mail on behalf of a real owner of the e-mail address.  
**SPF** record \(acronym for Sender Policy Framework\) is an effective and simple method which lets you avoid such issues. If your domain name has the correct SPF record, then you can be sure nobody is able to send fake e-mails on behalf of your domain name.  
  
The main idea of SPF record is that an owner of domain name publishes the information about IP addresses that are authorized to send mail from this domain name. The receiving server compares the information in the envelope sender address with the information published by domain name owner. If these details match then e-mail is delivered.  
  
**NOTES:**  


* SPF is not added to the domain DNS zone automatically. Thus, it is required to configure the proper record from the **Email Deliverability** menu.
* Sometimes cPanel automatically fetches incorrect server outgoing IP address. This happens when we have to change outgoing mail IP due to poor mail reputation or blacklists. Get in touch with us via [Live Chat](https://www.namecheap.com/support/live-chat/general.aspx) or [Ticket](https://support.namecheap.com/index.php?/Tickets/Submit) and we will gladly re-check if the correct IP is added to your SPF record.
* SPF record has its own specific syntax. It is strongly recommended to get familiar with [SPF record syntax documentation](https://www.spf-record.com/syntax) if you are going to customize the record manually. 
* SPF record is added to your domain DNS zone as TXT record. There are cases when you need to add another TXT record to verify your domain name ownership for some service. It is not recommended to modify existing SPF record, it is better to add a new one instead.  
* **DKIM Record**

**DKIM** \(DomainKeys Identified Mail\) is another way of e-mail authentication. This method uses information about domain which is published by the domain owner. That information allows receiving server to verify if the e-mail message was sent by legal owner of that domain name.  
  
Once TXT record which contains DKIM has been added to DNS zone, a special code is added to the headers of outgoing e-mails. Receiving servers compare these headers with the information in DNS zone and if it matches then the e-mail is delivered.  
  
**NOTE:** DomainKeys\(DK\) and DomainKeys Identified Mail \(DKIM\) are separate things.  
  
DomainKeys\(DK\) are not available on our shared servers as DK implementation was converted to DKIM and extended in a number of ways as of cPanel 11.32 and later releases.  
  
Some of the differences between DomainKeys and DKIM include:  


* multiple signature algorithms \(as opposed to just one available with DomainKeys\)
* more options with regard to canonicalization, that validates both header and body
* the ability to delegate signing to third parties
* the ability for DKIM to self-sign the DKIM-Signature header field – to protect against its being modified
* the ability for wildcard option on some parameters
* the ability to support [signature timeouts in DNS](http://stackoverflow.com/questions/5580136/differences-between-domainkeys-vs-dkim) 

If having DomainKeys for you is a must, we suggest upgrading to VPS/Dedicated server where you will be able to setup this feature.  
  
These simple actions will let you be sure that no one is able to send spam on your behalf and your e-mail will not be delivered to spam folders.  
In order to configure the SPF and DKIM records, follow the instructions below:  
  
Log into **cPanel** &gt; **Email** section &gt; **Email Deliverability** menu.  
For cPanel Basic Theme:  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/Deliverability.png)  
  
For cPanel Retro theme:  
  
****![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/Deliverability_1.png)  
****This section allows you to perform the following actions:  
1. **Repair** — this feature allows the system to repair a domain's invalid records:  
**NOTES**:

* This option is unavailable if the system does not control the domain's DNS records. Thus, you will be able to use the Repair option only in case your domain name is pointed to our **Shared hosting nameservers**.
* You cannot simultaneously update two or more domains whose records exist on the same zone. The bulk records update is possible only in case domains' records exist on separate zones.
* Reloading the interface does not interrupt the repair process. 

  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/repair_option1.png)  
In the window that appears upon clicking **Repair**,  you can review and confirm the system's recommendations for any invalid records. You can also **Copy** or **Customize** a suggested record before you approve the system's repairs. Click on **Repair** and the records will be added to the DNS zone of the domain/subdomain automatically.  
  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/repair_option2.png)  
  
This process can take up to **five minutes**, depending on the server. When the records are set up, you will receive a corresponding success message.  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/repair_option3.png)  
  
Allow some time to pass for the records to propagate and refresh the page afterwards. The **Email Deliverability Status** will be then changed to **Valid**:  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/repair_option4.png)  
  
  
2. **Manage** - this option allows you to manually configure a domain's mail-related DNS records.  
  
The **Manage the Domain** section already displays the properly-configured DKIM and SPF record values. So in most cases, you just need to **Copy** them and paste manually to the DNS zone of your domain. Alternatively, you can click **Install the suggested record** to have the SPF and DKIM records added to the DNS zone automatically:  
**NOTE**: The **Install the suggested record** option is available only in case your domain name is pointed to our **Shared hosting nameservers**.  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option1.png)After the record is installed, you will receive the confirmation message:  
  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option1r.png)  
In the **SPF** section, you will also have an option to **Customize** the system's recommended SPF record for a domain.  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option2.png)  
The interface displays the domain's current SPF name and value in the **Current "SPF" \(TXT\) Record** section, if one exists, and the system's recommendations in the **Suggested "SPF" \(TXT\) Record** section:  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option2r.png)  
You can configure the following settings:  
1. **Domain Settings -** this section allows you to define the hosts or MX servers allowed to send mail from your domain:  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option_spf1.png)  
  
2. **IP Address Settings** - this section allows you to add additional IP Address blocks to your SPF record. The system automatically includes your server's main IPv4 or IPv6 addresses in these lists:  
  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option_spf2.png)  
  
3. **Additional Settings** - this section allows you to modify additional SPF record settings.4. **Preview of the Updated Record**- this section displays what the updated SPF record will look like, based on its current modifications. Click the **Install a Customized SPF Record** tab to install the new record:  
![](https://namecheap.simplekb.com//SiteContents/2-7C22D5236A4543EB827F3BD8936E153E/media/manage_option_spf3.png)  
  
  
  
That's it!

