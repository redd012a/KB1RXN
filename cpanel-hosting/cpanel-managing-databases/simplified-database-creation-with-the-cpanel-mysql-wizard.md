# Simplified database creation with the cPanel MySQL Wizard

## Overview

This wizard guides you through the setup of a MySQL® database, user accounts, and user privileges. We recommend that you use this wizard to create your first database and user.

To create additional databases or users, you can also use the [_MySQL Databases_](https://documentation.cpanel.net/display/68Docs/MySQL+Databases) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Databases &gt;&gt; MySQL Databases_\).

## Set up a database

To set up a database, perform the following steps:

1. In the _New Database_ text box, enter a name for the database and click _Next Step_.

   Note:

   The system limits the database name to 64 characters. However, due to the method that cPanel & WHM uses to store MySQL database names, each underscore character requires **two** characters of that limit. Therefore, if your hosting provider enabled database prefixing, the maximum length of the database name is **63 characters**, which includes both the database prefix and the underscore character. Each additional underscore requires another **two** characters of that limit.

2. In the _Username_ text box, enter a name for the user who you wish to allow to manage the database.

   Important:

   To learn more about database username limits, click your database type: `MySQL MariaDB`

3. Enter and confirm the new password in the appropriate text boxes.

   Notes:

   * The system evaluates the password that you enter on a scale of 100 points. `0` indicates a weak password, while `100` indicates a very secure password.
   * Some web hosts require a minimum password strength. A green password _Strength_ meter indicates that the password is equal to or greater than the required password strength.
   * Click _Password Generator_ to generate a strong password. For more information, read our [Password & Security](https://documentation.cpanel.net/display/68Docs/Password+and+Security) documentation.

4. Click _Create User_.
5. Select the checkboxes that correspond to the privileges that you want to grant the user, or select _ALL PRIVILEGES._
   * For more information about user privileges, read the [MySQL documentation](http://dev.mysql.com/doc/).
6.  Click _Next Step_.

The system displays a message that states that you successfully set up the database and user account.

### Additional options

After you complete the database setup process, select one of the following options:

* _Add another database_ — Click to return to the beginning of the _MySQL Database Wizard_ interface to add more databases.
* _Add another MySQL Databases User_ — Click to open the [_MySQL Databases_](https://documentation.cpanel.net/display/68Docs/MySQL+Databases) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Databases &gt;&gt; MySQL Databases_\) to create additional user accounts and assign them to a database.
* _Return to Home_ — Click to return to the cPanel _Home_ interface.

{% hint style="info" %}
**Note:** When you use the _MySQL Database Wizard_ interface to add a user and a database, the system automatically grants the user access to the database. You do **not** need to use the _Add User to Database_ feature in the _MySQL Databases_ interface \(_cPanel &gt;&gt; Home &gt;&gt; Databases &gt;&gt; MySQL Databases_\).
{% endhint %}



