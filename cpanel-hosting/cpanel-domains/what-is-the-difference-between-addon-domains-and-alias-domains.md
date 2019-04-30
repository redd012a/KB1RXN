# What is the difference between addon domains and ‘alias’ domains?



### Addon and alias domains <a id="AddonDomains-Addonandaliasdomains"></a>

| Characteristic | Addon domains | Alias domains |
| :--- | :--- | :--- |
| The main domain appears in the address bar. | Yes | No |
| The domain uses the following Apache directive: | VirtualHost | ServerAlias |
| The domain uses separate logs. | Yes | No |
| The domain uses separate stats. | Yes | No |
| The system treats the domain as a subdomain \(other than the URL\). | Yes | No |
| This type of domain is ideal for multiple domains that share the same address. | No | Yes |

