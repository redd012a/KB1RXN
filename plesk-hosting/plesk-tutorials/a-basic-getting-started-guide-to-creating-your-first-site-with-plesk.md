# A basic getting started guide to creating your first site with Plesk

This section walks you through the steps of performing the most essential web hosting tasks with the help of Plesk. By the end of the tutorial you will have created a functional website, added a database and a mail account, and you will also have learned how to manage DNS records and back up your website.

## Step 1. Create Your First Website

To set up your first website, you need to follow these steps:

1. Register a domain name.
2. Add a domain in Plesk.
3. Create your website.

#### **Registering a Domain Name**

Think of the domain name as your business’ address. Your customers will use it to find you online, so make sure it is a good one. The best domain names are short, easy to type, and easy to remember. An example of a domain name is _example.com_. Registering a domain name can be done through one of the many organizations called domain registrars. Your hosting provider will usually be able to assist you in registering a domain name as well. Web hosting services are often bundled with domain name registration offers, and vice versa.

{% hint style="warning" %}
**Caution:** If you are a web hosting customer, make sure that when registering a domain name through your hosting provider, it is registered in your name. Otherwise, you may have trouble if you decide to change your hosting provider in the future.
{% endhint %}

#### **Adding a Domain in Plesk**

If you are a web hosting customer, your provider has probably already added your first domain for you. If they have not, contact your provider. If you are a web admin using the Power User view, you have configured your first subscription during the initial Plesk setup. Adding a domain in Plesk enables you to upload content, use Presence Builder, or install a content management system.

In the future, you will be able to add more domains, but for the purpose of this section, your first domain will suffice.

#### **Creating Your Website**

There are three ways to create the content for your website. Each has its advantages and disadvantages. Here is a short summary of all three:

* **Employ a professional designer and upload content.** This option guarantees you will get exactly what you want. However, it is also the most expensive one. The web designer will provide you with the files you will need to upload to your hosting account. You can do it using FTP or the File Manager. To learn how to do it, [**click here**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74379).
* **Use Presence Builder.** The Presence Builder tool that comes bundled with Plesk enables you to create websites using a web interface. You can use one of the provided templates to create a professional-looking website in a matter of minutes. To learn how to do it, [**click here**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74380).
* **Use a content management system.** Content management systems \(CMS for short\) are third-party applications that enable you to create and maintain a website. They are highly versatile, and come with a large number of optional add-ons. CMS offer a greater degree of customization as compared to Presence Builder but demand more technical knowledge from the user. To learn how to use a CMS, [**click here**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74381).

### Option A. Upload Content

If you have coded your website yourself, or employed a web designer to do it for you, you need to upload the website content to Plesk before the website becomes available on the Internet. Plesk gives you the option to upload content either using FTP, or the file manager. The instructions below explain how to do both – choose which option works best for you.

To publish a website using FTP:

1. Download an FTP client program. You can choose any FTP client you like. If you do not know what FTP client to choose, you can use FileZilla:
   * You can download FileZilla here: [https://filezilla-project.org/download.php?type=client](https://filezilla-project.org/download.php?type=client)
   * You can find FileZilla documentation here: [https://wiki.filezilla-project.org/Documentation](https://wiki.filezilla-project.org/Documentation)
2. Connect to your subscription on the server using the FTP client. To connect, you need the following information:
   * **FTP server address.** The FTP address should be _ftp://your-domain-name.com_, where your-domain-name.com is your site’s Internet address.
   * **FTP username.** This is identical to your system user name. Note that the system user name may differ from the username that you use for logging in to Plesk. To find what your system user name is, open the **Websites & Domains** tab and click **Web Hosting Access**. You will find it under **Username**. You can change your system user name if you wish.
   * **FTP password.** This is identical to your system user password. If you do not know what your system user password is, open the **Websites & Domains** tab and click **Web Hosting Access**. You can reset the password under **Password**.
3. Switch on the passive mode if you are behind a firewall. Refer to your FTP client documentation to learn how to enter the passive mode.
4. Upload the files and directories of your site to the `httpdocs` directory. If you use CGI scripts, place them in the `cgi-bin` directory.

To publish a website using the file manager:

1. On your computer, add the folder containing your website’s files to a .ZIP archive.
2. In Plesk Control Panel, go to **Files**, click the `httpdocs` folder to open it, click **Upload**, select the archive file, and click **Open**.
3. Once the file has been uploaded, click the checkbox next to it, click the **More** button, and select the **Extract Files** option.

   ![File\_Manager\_upload](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77044.png)

It is possible that the website you have uploaded requires a database to function. To learn how to create a database, [**click here**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74382).

### Option B. Create your Website in Presence Builder

To create a website using Presence Builder, go to **Websites & Domains**&gt; **Presence Builder** and click **Create Site**.

![WPB-create\_site](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77045.png)

Find more information on creating and editing websites in Presence Builder at [http://docs.plesk.com/current/customer-guide/](https://docs.plesk.com/en-US/12.5/redirect.html?book=customer-guide&page=70317.htm).

Creating your website in Presence Builder means that you do not need a database. Proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74389) to learn how to create a mail account in Plesk.

### Option C. Install a Content Management System

To create a website using a _Content Management System_ \(or _CMS_\), go to **Applications** &gt; **Install**.

![Application\_install](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77046.png)

Note that installing a CMS following the instructions above means that a database will be created for your website automatically. Proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74389) to learn how to create a mail account in Plesk.

## Step 2. Create a Database

Databases are relational structures used for storing data. Databases are indispensable in modern web hosting, and most of the popular CMSs require a database to operate. Plesk supports MySQL, MSSQL and PostgreSQL database servers, and enables you to add, remove and access databases, as well as manage database users.

If your website does not require a database, proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74389) to learn how to create a mail account in Plesk.

To create a database and a database user:

Go to **Databases** &gt; **Add Database**.

![Add\_database](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77047.png)

## Step 3. Create a Mail Account

The mail service enables Internet users to send email messages to each other. Plesk can function as your mail server. It also enables you to create mail accounts and manage them, including performing a number of common mail-related operations. Such operations include changing the password for a mail account, enabling automatic replies, and so on.

If you do not need to create a mail account, proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74390) to learn how to add a custom DNS record in Plesk.

To create a mail account, go to **Mail** &gt; **Create Email Address**.

![Create\_mail\_address](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77099.png)

## Step 4. Add a Custom DNS Record

DNS records serve to facilitate domain name translation and help visitors reach your website online. When a domain is created in Plesk, all the necessary DNS records are added automatically. However, Plesk also enables you to add custom DNS records, as explained below.

If you do not need to create a custom DNS record, proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74391) to learn how to back up your website.

To add a custom DNS record to the domain’s DNS zone, go to **Websites & Domains** &gt; **DNS Settings** &gt; **Add Record**.

![Add\_DNS\_record](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77100.png)

## Step 5. Back Up Your Website

It is always recommended to keep a backup copy of your websites in case their configuration or content becomes damaged or lost.

If you do not need to back up your website, proceed to the [**next step**](https://docs.plesk.com/en-US/onyx/quick-start-guide/plesk-tutorial.74376/#o74392) to learn how to change your password and log out of Plesk.

To access the backup function, do the following:

* If you are a hosting customer, go to **Websites & Domains** &gt; **Backup Manager** &gt; **Back Up**.
* If you are a server administrator and are using the power user view, go to **Backup Manager** &gt; **Back Up**.

  ![Customer\_backup](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77051.png)

## Step 6. Change Your Password and Log Out

If you are a web hosting customer, it is likely that the password you use to log in to Plesk was set up for you by your hosting provider. To change it, hover your mouse pointer over your user name located at the top of the page and click **Edit Profile**.

![Edit\_Profile](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77052.png)

Now that we have performed all the desired tasks, it is time to log out of Plesk. Hover your mouse pointer over your user name located at the top of the page and click **Log out**.

![Log\_out](https://docs.plesk.com/en-US/onyx/quick-start-guide/images/77053.png)

This concludes our tutorial. We hope it was useful, and encourage you to further explore Plesk and learn all the other ways it can make managing your web hosting account easier.

