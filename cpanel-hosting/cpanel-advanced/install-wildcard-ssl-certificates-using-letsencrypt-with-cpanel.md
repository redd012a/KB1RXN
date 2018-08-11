# Install Wildcard SSL Certificates using LetsEncrypt with cPanel

 are using our cPanel hosting, then we are now able to provide wildcard certificates completely free of charge.

## What is a Wildcard Certificate and do I need one?

A wildcard certificate is an SSL certificate that is valid for all subdomains of one or more domains. It can be identified by an `*.` prefix on any of the names it is issued for, e.g. `*.example.org`, `*.staging.example.org`

We suggest that the majority of users do not need wildcards. They are useful when:

* You have many \(10-100+\) subdomains or combinations of subdomains
* You don’t know what subdomains will exist, e.g. when you dynamically give each customer/user their own subdomain, e.g. when you have a subdomain-based multi-site
* You regularly create new subdomains \(at least on a monthly basis\)
* You are using a wildcard DNS record and need to protect all possible domains using SSL

**Unless your requirements resemble one or more of those listed above, we recommend you stick to non-wildcard certificates. They are simpler, faster to issue and safer to manage.**

## Prerequisites

### **DNS Validation is required: Your DNS must be hosted with cPanel**

Due to Let’s Encrypt policy, wildcard certificates _must_ use DNS-based validation.

This means that your domain _must_ have its DNS hosted within your cPanel’s / our nameservers, because cPanel needs to be able to create TXT records to demonstrate control of your domain. If your domain has its DNS externally hosted, you will not be able to issue wildcard certificates.

The choice of validation method will be presented to you when you go to issue your certificate.

## How to issue a Wildcard Certificate

### **1. Open the Lets Encrypt SSL interface**

Visit the Lets Encrypt SSL interface in cPanel, and select which domain you would like to issue a certificate for, as per the [user guide](https://letsencrypt-for-cpanel.com/docs/for-users/user-guide/).

### **2. Select the DNS validation method**

![Selecting DNS-01 validation](https://letsencrypt-for-cpanel.com/docs/select-validation-method.png)

### **3. Select which domains you would like wildcards for:**

Check the “Include Wildcard?” column to add the wildcard variant of any domain to your certificate request. You may include as many combinations of wildcards and other domains as you like on a single certificate.

Please take note, if you would like a certificate to be valid for `mail.l33t.website` as well as `*.mail.l33t.website`, you must tick both ‘Include?’ and ‘Include Wildcard?’, as the wildcard will not match the domain on its own.

![Selecting wildcard domains](https://letsencrypt-for-cpanel.com/docs/select-wildcard.png)

### **4. Issue**

Press the **Issue** button and wait.

If you experience a failure, please double check that your domain is using the nameservers of your cPanel hosting service, rather than being externally hosted \(such as on Cloudflare or Route53 or at your domain registrar\).

