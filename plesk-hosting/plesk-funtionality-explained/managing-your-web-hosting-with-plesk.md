# Managing your Web Hosting with Plesk

## Adding Domains

If your subscription allows it, you can create more than one domain on a single subscription. The newly added domain will share the subscription’s resources with all other domains belonging to the same subscription. However, in all other respects the newly created domain will be independent from the principal one – it will have its own web hosting and DNS settings, databases, mail accounts, and so on.

Adding a new domain is helpful in the following scenarios:

* You want to create an additional website that is unrelated to any of the websites you already own, with its own name, web content, mail accounts, and so on. Note that in this scenario, unless you already have another second-level domain name registered, you will need to register one for the new website. A second-level domain name consists of a proper name and a top level domain suffix \(called TLD for short\), such as .com or .net. _example.com_ is an example of a second-level domain. You may be able to register a domain name through your provider. Alternatively, you can purchase one from a domain registrar of your choice.
* You want to transfer a domain already hosted at a different provider. In this scenario you may need to contact your domain registrar to change the authoritative name servers for the domain name of the website you want to transfer to Plesk name servers. You will also need to transfer website content – you can upload it via FTP or the File Manager, as described in the **Uploading Content** section.
* You want to set up a website that will redirect visitors to a different website. Some possible reasons for setting up such redirection are listed in the **Adding Domain Aliases** section. You need a separate domain name for the domain alias.

To add a new domain, go to **Websites & Domains** &gt; **Add Domain**.

![Add\_domain](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77058.png)

## Adding Subdomains

If your subscription allows it, you can create one or more subdomains, or third-level domains, for each of your domains. Subdomains share all the subscription’s resources with all the other domains and subdomains belonging to the same subscription. However, every subdomain can have its own web hosting and DNS settings.

Adding a new subdomain is helpful in the following scenarios:

* You want to logically organize the structure of your website. For example, you can display the information about your company at _info.example.com_, or have your web store accessible at _store.example.com_.
* You want to host a large number of simple websites and do not want to purchase a separate domain name for each of them. For example, you can host personal websites using addresses like _johndoe.example.com_ and _janedoe.example.com_.

To add a new subdomain, go to **Websites & Domains** &gt; **Add Subdomain**.

![Add\_subdomain](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77059.png)

## Adding Domain Aliases

If your subscription allows it, you can create one or more domain aliases. Domain aliases do not have any content of their own, but instead redirect to a different website when visited. Note that unless you already have another second-level domain name registered, you will need to register one for the domain alias. You may be able to register a domain name through your provider. Alternatively, you can purchase one from a domain registrar of your choice.

Adding a new domain alias is helpful in the following scenarios:

* You want to make sure that the visitors can find your website regardless of the TLD they use. For example, you can register _example.net_and _example.org,_ and use them as domain aliases pointing to your website _example.com_.
* You want to make sure that visitors who mistype your domain name can find your website. For example, you can register _exmaple.com_and use it as a domain alias pointing to your website _example.com_.
* You want to change the domain name of your website but also want visitors who use your old domain name to be able to find your website. For example, you want to change the domain name of your website from _example.com_ to _anotherexample.com._ You can configure the _example.com_ name to be a domain alias pointing to your new website _anotherexample.com_.

To add a new domain alias, go to **Websites & Domains** &gt; **Add Domain Alias**.

![Add\_domain\_alias](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77060.png)

## Setting Up Custom Error Pages

Whenever the web server encounters an error that prevents it from correctly displaying the page of your website a visitor has requested, a special error page is displayed along with the relevant error code. By default, such pages are often generic and may not be sufficiently informative. You can replace the standard error pages with custom ones.

### **Setting Up Custom Error Pages on Linux**

1. Go to **Websites & Domains** &gt; **Hosting Settings**.
2. Select the **Custom error documents** checkbox and click **OK**.

   ![Custom\_error\_pages\_Linux](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77061.png)

3. Connect to your FTP account, and go to the `error_docs` directory.
4. Edit or replace the respective files. Be sure to preserve the correct file names:
   * 400 Bad File Request – bad\_request.html
   * 401 Unauthorized – unauthorized.html
   * 403 Forbidden/Access denied – forbidden.html
   * 404 Not Found – not\_found.html
   * 405 Method Not Allowed – method\_not\_allowed.html
   * 406 Not Acceptable – not\_acceptable.html
   * 407 Proxy Authentication Required – proxy\_authentication\_required.html
   * 412 Precondition Failed – precondition\_failed.html
   * 414 Request-URI Too Long – request-uri\_too\_long.html
   * 415 Unsupported Media Type – unsupported\_media\_type.html
   * 500 Internal Server Error – internal\_server\_error.html
   * 501 Not Implemented – not\_implemented.html
   * 502 Bad Gateway – bad\_gateway.html
   * 503 Service Temporarily Unavailable – maintenance.html

The web server will start using your error documents after it is restarted.

### **Setting Up Custom Error Pages on Windows**

1. Go to **Websites & Domains** &gt; **Hosting Settings**.

   Select the **Custom error documents** checkbox and click **OK**.

   ![Custom\_error\_pages\_Windows](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77062.png)

2. Click **Virtual Directories** and open the **Error Documents** tab. The list of error documents for the root web directory will be displayed. These are used for all web pages of the selected site. If you want to customize error pages for a specific virtual directory, navigate to that directory first.
3. Click the error document you want to change. The following options are available:
   * To use the default document provided by IIS for this error page, select **Default** from the **Type** menu.
   * To use a custom HTML document located in the `error_docs` directory situated in the virtual host directory of the domain, select **File** from the **Type** menu and specify the file name in the **Location** field.
   * To use a custom HTML document located in a directory other than `error_docs`, select **URL** from the **Type** menu and enter the path to your document in the **Location** field. The path must be relative to the virtual host root \(that is, the `%plesk_vhosts%\<domain_name>\httpdocs folder`\).

     For example, you have created a file named `forbidden_403_1.html` and saved it in the `my_errors` directory located in the `httpdocs directory`. To use this file as an error document, you need to type the following path into the **Location** field: `/my_errors/forbidden_403_1.html`.

**Note:** You can use FTP or File Manager in Plesk to upload your custom error document to the server. By default, all error documents are stored in the `%plesk_vhosts%\<domain_name>\error_docs\` directory.

The web server will start using your error documents after it is restarted.

## Setting Up HTTP 301 Redirection

Plesk provides two ways of setting up the search engine friendly HTTP 301 redirection from one website to another. This allows preserving search engine rankings of the website to which visitors are redirected. For example, if you set up HTTP 301 redirection from _example.com_to _www.example.com_, search engines will treat both www and non-www versions as the same site. If you use HTTP 302 redirection instead, the www and non-www versions will be treated as different sites. As a result, rankings will be split between them.

To set up HTTP 301 redirection using domain aliases, go to **Websites & Domains** &gt; **Add Domain Alias**.

![Add\_domain\_alias](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77063.png)

To set up HTTP 301 redirection using forwarding hosting type, go to **Websites & Domains** &gt; **Add Domain**.

![Add\_domain](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77064.png)

## Configuring the Preferred Domain

As a rule, any website is available using both a URL with a www prefix \(such as _www.example.com_\) and one without it \(such as _example.com_\). We recommend that you pick one and always redirect visitors from the other. Typically, the non-www version is chosen to accept all visitors. As an example, if you configure the non-www version \(_example.com_\) as the preferred domain, a visitor will be redirected to _example.com_ even if they type _www.example.com_ in their browser address bar.

To configure or disable the preferred domain, go to **Websites & Domains** &gt; **Hosting Settings**.

![Hosting\_Settings](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77065.png)

Plesk uses the search engine friendly HTTP 301 code for the redirection. This allows for preserving search engine rankings of your site \(preferred domain\). If you disable the redirection, search engines will treat both www and non-www versions as different sites. As a result, rankings will be split between them.

## Setting the Default Homepage

### **To change the default index page in Plesk for Linux**

1. Go to **Websites & Domains** &gt; **Apache & Nginx Settings**.

   ![Apache&amp;Nginx](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77066.png)

2. Select the **Enter custom value** option in the **Index files** section. Specify the file name or names to be used as the default page. You can specify more than one, separating the file names from each other with white spaces. For example, if you specify “index.htm index.php”, the web server will serve **index.htm** as the default page. If the file with such name is not found, **index.php** will be served.

   ![Apache\_Index\_files](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77067.png)

### **To change the default index page in Plesk for Windows**

1. Go to **Websites & Domains** &gt; **IIS Settings.**

   ![Windows\_IIS\_settings](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77068.png)

2. Select the **Enter custom value** option in the **Default documents** section. Add or remove file names from the list. The web server will be looking for the default page file starting from the topmost entry in the list and continuing downwards. For example, if you specify “index.htm” with “index.php” right underneath it, the web server will serve index.htm as the default page. If the file with such name is not found, index.php will be served.

![Windows\_default\_documents](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77069.png)

## Changing the Document Root Directory

Every domain in Plesk created with website hosting has its own directory created on the server’s file system. By default the path to the directory is as follows:

* On Linux: `/var/www/vhosts/<domain_name>`
* On Windows: `C:\Inetpub\vhosts\<domain_name>`

This folder contains the document root directory, that is, the folder where all the domain’s web content is stored. By default it is the `httpdocs` folder, but it can be changed in Plesk.

To change the document root directory, go to **Websites & Domains**&gt; **Hosting Settings** and ****change the directory name in the **Document root** field.

![Document\_root](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77070.png)

## Selecting PHP Version

To change the PHP version, go to **Websites & Domains** &gt; **Hosting Settings** and select the required version in the **PHP version** menu.

![PHP\_version](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77071.png)

## Configuring PHP Settings

To change PHP settings, go to **Websites & Domains** &gt; **PHP Settings**.

![PHP\_Settings](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/75586.png)

## Selecting ASP.NET Version

To change the ASP.NET version, go to **Websites & Domains** tab &gt; **Hosting Settings** and select the required version in the **Version** menu near the **Microsoft ASP.NET support** checkbox.

![ASP\_Net\_version](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77072.png)

## Setting MIME Types

Multipurpose Internet Mail Exchange \(MIME\) types instruct a web browser or a mail application how to handle files received from the server. For example, when a web browser requests an item on a server, it also requests the MIME type of the object. Some MIME types, such as graphics, can be displayed inside the browser. Others, such as word processing documents, require an external application to be displayed.

By setting custom MIME types you can determine what applications are used to open a particular type of file on the client side.

To configure MIME types in Plesk for Linux, go to **Websites & Domains** &gt; **Apache & Nginx Settings**.

![Apache&amp;Nginx](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77073.png)

To configure MIME types in Plesk for Windows, go to **Websites & Domains** &gt; **IIS Settings**.

![Windows\_IIS\_settings](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77074.png)

Then specify MIME types associating file extensions with file types. For example: “text/plain .mytxt”.

![MIME\_types](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77075.png)

