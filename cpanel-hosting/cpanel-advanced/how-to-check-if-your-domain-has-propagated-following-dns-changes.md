# How to check if your domain has ‘propagated’ following DNS changes

If you have recently updated your domain name to use new DNS records, or have updated your nameservers entirely, then you can check the propagation status using the following website…

https://www.whatsmydns.net/

**TIP:** DNS propagation nowadays is mostly gibberish – most providers will tell you DNS propagation can take up to 72 hours. This is rarely the case, and propagation completes in less than an hour globally.

What you may find is that your local machine / network is showing the incorrect DNS records, whilst the ‘whatsmydns.net’ service shows the propagation has completed to an alternative address.

If that is the case, you can do one of two things…

[Flush your DNS caches](https://brixly.uk/learn-article/flush-local-machines-dns-cache/)

[How to use the Google Public DNS service for better DNS lookups](https://brixly.uk/learn-article/use-google-public-dns-faster-dns-lookups/)  


