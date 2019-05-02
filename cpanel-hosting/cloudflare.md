# Cloudflare

Any website can deploy CloudFlare, regardless of your underlying platform. By integrating closely with Vimzaa, we make the process of setting up CloudFlare "1 click easy" through your existing Vimzaa cPanel dashboard. Just look for the CloudFlare icon, choose the domain you want to enable, and click the orange cloud. That's it!

## Cloudflare Railgun™

### What is Railgun?

Railgun ensures that the connection between your origin server and the Cloudflare network is as fast as possible.

Railgun is a WAN optimization technology that we offer our hosting customers in partnership with a company called CloudFlare.

CloudFlare’s Railgun technology greatly speeds up the delivery of non-cached pages. While CloudFlare automatically caches 65% of the resources needed to make up a page, 35% can't be cached because the resources are dynamically generated or marked as 'do not cache'. That 35% is often the initial HTML of the page that must be downloaded first. CloudFlare Railgun speeds this remaining 35%.

### What are the benefits of Railgun?

Websites running Railgun show a 143% improvement in HTML load times and a 90% decrease in Time To First Byte \(TTFB\) responses.

### How does Railgun work

Railgun opens a secure, tunneled connection between the CloudFlare network and your host’s origin server where the connection only sends differences from the last request. This is similar to how video encoding works. The markup of websites does not change that frequently from one request to the next. Instead of transferring the entire request between CloudFlare and the origin server, Railgun will transfer only the changes in markup from one request to the next. This cuts down on bandwidth, transfer time, and overall page load times. Railgun caches these differences in memory to make page processing as fast as possible.

### What kind of sites can use Railgun?

Any website can benefit from the performance improvements Railgun offers, especially dynamic sites.

### How much does Railgun cost?

We have partnered with CloudFlare to make Railgun both easy and affordable. If you purchase Railgun directly through CloudFlare, it costs $200/month. However, we have partnered with CloudFlare and are offering Railgun to our customers for free with thier shared hosting plan.

### How do I enable Railgun on my site?

To enable Railgun, follow the steps given below:

- Login to cPanel,  
- Go to Cloudflare \( by clicking Cloudflare Icon\)  
- Login/Signup to Cloudflare Account and provision your domain either by CNAME Method or using Cloudflare DNS \(Full Zone\) `(You may skip this step, if you are already logged in)`  
- Under `Overview` Turn on the Railgun.

### What if I’m having issues enabling Railgun?

If you experience issues when enabling Railgun, please [contact us](https://vimzaa.com/contact-us.php).

### I’m not a CloudFlare customer, can I still use Railgun?

No. You need to be a CloudFlare customer in order to use Railgun. you can follow the above steps to use Railgun.

### I’m seeing an error on my site and I think Railgun is causing it, what should I do?

If you are using Railgun via cPanel, you can turn it off directly from your control panel. Otherwise, log into your CloudFlare account, go to Performance Settings and turn Railgun off from there. Please file a bug report with a detailed description [here](https://support.cloudflare.com/anonymous_requests/new).

### Remind me, what is CloudFlare?

CloudFlare is a third party service that we offer to our hosting customers. CloudFlare provides performance, security and availability to web properties. CloudFlare runs a globally distributed network where they automatically cache static content, filter malicious traffic and help offload big spikes in traffic. On average, a site loads twice as fast, uses 65% fewer server resources and has and additional layer of secuirity.

