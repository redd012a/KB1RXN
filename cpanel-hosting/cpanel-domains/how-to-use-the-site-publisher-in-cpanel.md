# How to use the Site Publisher in cPanel

```text
cPanel > Home > Domains > Site Publisher
```

### Overview <a id="SitePublisher-Overview"></a>

This interface enables you to quickly create a simple website, even if you have never created a website before. When you use this interface, you will select an appropriate template for your website, and then enter the website content that the template requests.

For example, you can use this interface to create a simple website with your business’s information, or to create a placeholder page while you prepare a more elaborate website.

Note:

Hosting providers and third-party developers can create and add additional Site Publisher templates. For more information, read our [Guide to Site Publisher Templates](https://documentation.cpanel.net/display/SDK/Guide+to+Site+Publisher+Templates) documentation.

### Create or modify a Site Publisher website <a id="SitePublisher-CreateormodifyaSitePublisherwebsite"></a>

Note:

When you select an option, the interface automatically hides that section of the interface and displays the next section. To return to a section, click that section’s title.

To create or modify a Site Publisher website for one of your domains, perform the following steps:

1. Select a domain from the list of available domains, addon domains, and subdomains.
   * If you only own a single domain, or if you accessed this interface via a link after subdomain or addon domain creation, the system automatically selects that domain and proceeds to the next step.
   * For more information about domain selection, read the [Select a Domain](https://documentation.cpanel.net/display/68Docs/Site+Publisher#SitePublisher-Domain) section of this document.
2. Select a template from the available options.
   * The _Select a Template_ section of this interface displays a preview image, name, and description for each available Site Publisher template.
   * If you selected a domain that already uses a Site Publisher website, the system preselects the current template.
3. Enter or update the desired website content.

   Note:

   The template that you select determines the content that you enter in the _Customize and Publish_ section.

4. Click _Publish_. A confirmation message will appear with a link to your new website.
5. Warning:

   If the directory that will contain your Site Publisher website already contains other files or directories, the system will perform the following actions when you click _Publish_:

   1. Back up the directory’s contents. For more information, read the [Site Publisher files](https://documentation.cpanel.net/display/68Docs/Site+Publisher#SitePublisher-files) section below.
   2. Delete any existing files that use the same filenames as your new Site Publisher website’s files.
   3. Save the new website’s files to the directory.

   Note:

   You can also click the following helpful links for other common tasks within your cPanel account:

   * _Add an email account._ — Create and manage email addresses in cPanel’s [_Email Accounts_](https://documentation.cpanel.net/display/68Docs/Email+Accounts) interface \(_cPanel &gt;&gt; Home &gt;&gt; Email &gt;&gt; Email Accounts_\).
   * _Manage my website’s files_. — Upload and manage files in cPanel’s [_File Manager_](https://documentation.cpanel.net/display/68Docs/File+Manager) interface \(_cPanel &gt;&gt; Home &gt;&gt; Files &gt;&gt; File Manager_\).
   * _Connect to this website with Web Disk._ — Create Web Disk accounts in cPanel’s [_Web Disk_](https://documentation.cpanel.net/display/68Docs/Web+Disk) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Files &gt;&gt; Web Disk_\) to upload and manage files from your local computer.
   * _Publish another Site Publisher website_. — Use this interface to create another Site Publisher website.

#### Select a Domain <a id="SitePublisher-DomainSelectaDomain"></a>

The _Select a Domain_ section of the interface lists the domain name and website directory \(document root\) for every domain that your cPanel account owns. If a domain currently uses a Site Publisher website, the interface also lists the website’s template’s name.

* Click the domain name to open the domain in a new browser window.
* Click the website directory to open that directory in cPanel’s [_File Manager_](https://documentation.cpanel.net/display/68Docs/File+Manager) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Files &gt;&gt; File Manager_\) in a new browser window.

If your cPanel account owns a large number of domains, the interface automatically paginates the table. Click the page numbers in the top right corner of the section to navigate between pages of domains, or use the _Search_ text box at the top of the list to search for a domain.

### Site Publisher files <a id="SitePublisher-SitePublisherfiles"></a>

When you publish a Site Publisher website, cPanel automatically performs the following actions:

1. The script saves a copy of the domain’s document root’s current contents as a tarball in the `/home/user/site_publisher/backups/` directory, where `user` represents your cPanel account’s username.

   Note:

   If the system encounters a file system or file quota error during this step, it will **not** save the tarball and will **not** publish the new Site Publisher website.

2. The system deletes any existing Site Publisher backups that are more than 30 days old.
3. The system generates the new Site Publisher website’s files and stores them in the domain’s document root.
   * If one of the new website’s files conflicts with an existing file, the system overwrites the existing file with the new file.
   * If the system encounters an error during this step, it restores the website’s original contents from the backup tarball and does **not** publish the new Site Publisher website.
   * The system saves configuration information for the new website in the `/home/user/site_publisher/configurations/` directory, where `user` represents your cPanel account’s username. It saves this file as the `home-user-public_html-example.com.json` file, where `home-user-public_html-example.com` represents the Site Publisher website’s target directory, with hyphens \(`-`\) instead of slashes \(`/`\).

     Important:

     The configuration file stores all of the data for your Site Publisher website. We **strongly** recommend that you do **not** modify this file directly. Instead, always use cPanel’s _Site Publisher_ interface \(_cPanel &gt;&gt; Home &gt;&gt; Domains &gt;&gt; Site Publisher_\) to modify Site Publisher websites.

Your selected template determines the other files that your website uses. These files may include HTML files, images, or other types of files.

* For information about template development, read our [Guide to Site Publisher Templates](https://documentation.cpanel.net/display/SDK/Guide+to+Site+Publisher+Templates) documentation.
* For more information about individual templates, contact your hosting provider or the template creator.

