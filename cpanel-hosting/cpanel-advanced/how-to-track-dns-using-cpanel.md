# How to track DNS using cPanel

Network Tools allow a user to find out information about any domain, or to trace the route from the server your site is on to the computer you are accessing cPanel from. Finding out information about a domain can be useful in making sure your DNS is set up properly as you will find out information about your IP address as well as your DNS.

{% code title="Location under cPanel" %}
```text
cPanel > Home > Advanced > Track DNS
```
{% endcode %}

### Overview <a id="TrackDNS-Overview"></a>

This interface contains tools to help you retrieve network information. For example, you can look up an IP address or trace the route from your computer to the computer that hosts your website.

### Domain Lookup <a id="TrackDNS-DomainLookup"></a>

The _Domain Lookup_ tool executes the `host domain` command, where `domain` represents a specific domain. This command resolves an IP address from a specified domain name, and returns general DNS information about the server.

To look up a domain, perform the following steps:

1. Enter the domain to look up in the `Enter a domain` _to `look up`_ text box.
2. Click `Look Up`.

The domain’s mail servers and IP address will display. You can also view the domain’s DNS information under the `Zone Information` heading.

### Trace Route <a id="TrackDNS-TraceRoute"></a>

The `Trace Route` function traces the route that your computer takes to access your website. This function displays how many servers through which your data passes before it reaches your website. This information also includes the amount of time that your computer requires to reach the server.

To trace the route to your server, click `Trace`. The interface will display the pathways that your computer follows to reach your server.

You can use this information to find problem servers within your path.

Note:You may not possess access to this function. Contact your system administrator for more information about how to use the `Trace Route` function.

