# Correct SPF Records

Your service provider is now using SPAM Experts to send email from the hosting server on which your account is located. Correct Sender Policy Framework \(SPF\) records need to be configured in your DNS settings to ensure that Internet receivers will properly identify and receive your email. This article describes the DNS records you must add.

### DNS Records

The following records are needed for SPF to work correctly. Replace _example.com_ with your own domain name:

| **Location** |   **Type** |   **Value** |
| :--- | :--- | :--- |
| example.com |   TXT |   v=spf1 +a +mx +ip4:&lt;your-server-ip&gt; -all |
|  |  |  |

If you already have an SPF record, leave it. Make sure to add it BEFORE the “all” mechanism as “all” always matches and typically goes at the end of the SPF record.

