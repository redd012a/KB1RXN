# How to create custom ‘error pages’ in cPanel



An error page informs a visitor when there is a problem accessing your site. Each type of problem has its own code. For example, a visitor who enters a nonexistent URL will see a 404 error, while an unauthorized user trying to access a restricted area of your site will see a 401 error.

Basic error pages are automatically provided by the web server \(Apache\). However, if you prefer, you can create a custom error page for any valid HTTP status code beginning in 4 or 5.

{% code-tabs %}
{% code-tabs-item title="Location Under cPanel" %}
```text
cPanel > Home > Advanced > Error Pages
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Overview {#ErrorPages-Overview}

Error pages inform visitors about problems when they attempt to access your site. Each problem has its own status code \(for example, `404`\) and error page.

The web server automatically provides basic error pages, but the _Error Pages_ interface allows you to define custom error pages for any [HTTP status code](https://documentation.cpanel.net/display/CKB/HTTP+Error+Codes+and+Quick+Fixes).

### Edit an error page {#ErrorPages-Editanerrorpage}

To customize an error page, perform the following steps:

1. If this account manages more than one domain, select the domain for which you wish to edit an error page from the _Managing:_ menu.
2. Click the error status code for which you wish to edit its error page.
   * If you do not see the desired error status code in that list, click the _Show All HTTP Error Status Codes_ tab. Then, click on the desired error status code.
3. Enter a message in the text box.
   * To display information on the error page about the visitor who accessed your site, click the appropriate buttons for the information that you wish to display.
   * Enter additional HTML code to further customize your error pages.
4. Click _Save_.

