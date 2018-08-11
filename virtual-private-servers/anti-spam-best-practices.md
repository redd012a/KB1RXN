---
description: A detialed overview on how to mitigate email spam.
---

# Anti-Spam Best Practices

## Introduction

This article contains the best practices for outgoing email from your server to the internet. These practices must be followed so your emails do not get filtered, blocked, or marked as spam by us or other anti-spam organisations.

## Why do we apply protective measures to outgoing emails?

For every IP available with our products and services, as an internet service provider, Vimzaa Web Hosting Services will register and reserve it with organisations such as RIPE or ARIN. This means that we appear as the IP abuse contact for litigation in the WHOIS database.

If an IP is reported to organisations such as Spamhaus and SpamCop?, which work to combat spam, malicious websites and phishing, then the reputation of the entire Vimzaa Web Hosting Services network is at stake.

It is therefore important that Vimzaa Web Hosting Services takes care of the reputation, quality and security of the network, which also forms an important part of your service.

## How does the protection system work?

Our system is based on the Vade Retro anti-spam technology.

## What to do after receiving an email alert

Important steps to take on receiving a block alert BEFORE the affected IP can be unblocked. 1. stop sending email \(e.g. stop all mail software such as qmail, Postfix, Sendmail etc.\) 2. check the email queue \(e.g. qmHandle for qmail, postqueue -p for Postfix\) 3. analyse your logs using the Message-ID found in the block alert

## Can I get whitelisted?

It is not possible to get a whitelisting, i.e. a filtering exclusion on the outgoing emails from your server.

We can only assist you with the logs diagnosis, if the Message-IDs are unknown and not part of your legitimate emails or mailing lists.

## False Positives

If you have checked and found that Message-ID are from your legitimate email, you should then ensure that your email messages comply with the RFC and the Best Practices indicated below. If they do comply, you can inform us by sending a sample of your email \(including header\). Our technical support team will then assist you with the next steps. Simply call our support line or contact us via the email support interface in your manager.

## RFC and Best Practices

RFCs \(Request For Comments\) are documents intended to describe technical aspects of the internet. They are produced and published by the IETF \(Internet Engineering Task Force\), a group which basically produces and defines standards.

For more information, see: RFC, IETF and Internet Draft

Best practices are recommended methods which are often based on these documents and are intended to advise you on the best way to proceed. In this instance, this means the basic rules to follow so that your emails are not marked as spam.

## Sending Volume

If your outgoing email volume is very high, you are advised to: 1. reserve an IP block dedicated solely to email usage, 2. provide an 'abuse' address on this block in order to receive complaints, 3. configure reverses on all IPs correctly

This operation will enable you to simultaneously isolate the IP and domain reputation if you send emails for various domains, to receive the complaints, and thus do what is necessary to get unblocked by various organisations. It also enables you to locate a problem more quickly on a form that uses domain X or Y, as the emails are not sent out from the same IP and don't have the same reverse.

## Email Content

Avoid using spammer keywords in your emails such as “buy” and “last chance”, and avoid capital letters, impersonal subjects, exclamation marks, and % discounts.

Don't forgot to provide an unsubscribe link for people who have not requested to receive your email or who believe it to be illegitimate.

Be particularly careful to ensure that your emails contain the sender's address \(or an alias\), a subject, and a correct ratio of text, images and links in the body of the message.

The text vs. image and text vs. link ratio must be high. Don't overload the email with hypertext links and avoid Javascript.

## FBL - Feedback Loop

This system will enable you to follow up on feedback provided by some internet service providers directly, informing you that their users have marked your message as illicit, and that it has thus been classified as spam. This will enable you to interact with these ISPs directly concerning your reputation. Some FBLs:

* Yahoo
* AOL Postmaster
* SpamCop
* Outlook & live.com

## Authentication

Some authentication services enable you to protect your reputation.

### **Sender-ID**

An email authentication technology developed by Microsoft which validates the authenticity of your domain name by verifying the IP address of the sender. This technology is based on the IETF standard: RFC4406

### **SPF**

Sender Policy Framework is a standard for verififying the domain of the sender. It is based on RFC4408 and consists of adding an SPF or TXT field to the domain DNS, which contains the list of IPs authorised to send emails from this domain.

### **Reverse DNS**

Reverse enables your IP to be "translated” into your domain. That allows the domain associated with the IP address to be found.

### **DKIM**

DKIM This standard is described in RFC4871.

AOL, Google \(Gmail\) work on this basis. Official website: DKIM

### How to unblock IP?

To unblock your IP, you must submit a ticket to the technical department with information on the IP that was blocked and what you have done to stop the spam.

If spam continues after block is removed, it would result in a longer spam block, reinstallation of the entire sever without prior notice, suspension of service, termination of service, or a combination of multiple consequences.

