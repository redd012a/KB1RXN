# Manage MySQL Database in cPanel

## Overview

Use this interface to create, manage, and delete MySQL® databases and database users.

Notes:

* We recommend that you use the [_MySQL Database Wizard_](https://documentation.cpanel.net/display/68Docs/MySQL+Database+Wizard) __interface \(_cPanel &gt;&gt; Home &gt;&gt; Databases &gt;&gt; MySQL Database Wizard_\) to create your **first**database and user.
* The maximum length of the database name is 64 characters.
  * Due to the method that cPanel & WHM uses to store MySQL database names, each underscore character requires **two** characters of that limit.
  * If you enable database prefixing, the maximum length of the database name is **63 characters**, which includes the database prefix and the underscore character. Each additional underscore requires another **two** characters of that limit.
* To enter information in an existing database, use the _phpMyAdmin_ interface \(_cPanel &gt;&gt; Home &gt;&gt; Databases &gt;&gt; phpMyAdmin_\).

Important:

Do **not** use phpMyAdmin to create databases or database users.

## Create a database

To create a database, perform the following steps:

1. In the _New Database_ text box, enter a name for the database.

   Note:

   If your hosting provider has enabled database prefixing, up to the first eight characters of your cPanel account username and an underscore character \(_\__\) will precede the _New Database_ text box. The system automatically prepends the database name that you enter with this prefix.

2. Click _Create Database_. A new interface will appear.
3. Click _Go Back_. The new database appears in the _Current Databases_ table.

## Modify Databases

If you experience problems with a database, check your databases for errors.

### Check a database

To check a database for errors, perform the following steps:

1. In the _Check Database_ menu, select the database that you wish to check.
2. Click _Check Database_. A new interface will appear, and the system will check whether the database functions correctly.
   * If the system detects a problem in the database, it displays the name of the corrupt table.
   * If the _Check Complete_ message displays, the database functions correctly.
3. Click _Go Back_ to return to the main interface.

## Repair a database

If one of your databases is corrupt, you can attempt to repair it.

To repair a database, perform the following steps:

1. In the _Repair Database_ menu, select the database that you wish to repair.
2. Click _Repair Database_. A new interface will appear, and the system will attempt to automatically repair the database.
   1. If the system cannot repair the database, it will attempt to determine the source of the corrupt data.
   2. If the _Repair Complete_ message displays, the system successfully repaired the database.
3. Click _Go Back_ to return to the main interface.

## Current Databases

The _Current Databases_ table lists the following information for each database in your account:

* _Database_ — The name of the database.
* _Size_ — The size of the database.
* _Privileged Users_ — The users who can manipulate the database.

  Note:

  When you modify database users, make **certain** that you modify the user’s access to the correct database. Users may have access to more than one database.

  * To remove a user from a database, click the trashcan icon \(![](https://documentation.cpanel.net/download/attachments/1793896/image2016-11-1%2011%3A27%3A56.png?version=1&modificationDate=1512101436689&api=v2)\) for the desired user, and then click _Revoke User Privileges from Database_.
  * To modify a user’s [privileges for a specific database](http://dev.mysql.com/doc/), click the desired username, select and deselect checkboxes to configure the desired privileges, and then click _Make Changes_.

* _Actions_ — The available actions for this database. Click the appropriate icon in this column to rename or delete a database.

### Rename a database

{% hint style="warning" %}
Warning:

* It is potentially dangerous to rename a MySQL database. We **strongly** recommend that you perform a backup of the MySQL database before you attempt to rename it.
* When you rename a database, the system terminates all active connections to the database.
* You **must** manually update configuration files and applications to use the new database name.
* The system requires more time to rename larger and more complex databases.
{% endhint %}



To rename a database, perform the following steps:

1. In the _Current Databases_ table, click _Rename_ for the desired database.
2. Enter the new database name in the _New name_ text box.
3. Click _Proceed_.

MySQL does **not** allow you to rename a database. When cPanel & WHM “renames” a database, the system performs the following steps:

1. The system creates a new database.
2. The system moves data from the old database to the new database.
3. The system recreates grants and stored code in the new database.
4. The system deletes the old database and its grants.

Warning:

* If **any** of the first three steps fail, the system returns an error and attempts to restore the database’s original state. If the restoration process fails, the API function’s error response describes these additional failures.
* In rare cases, the system creates the second database successfully, but fails to delete the old database or grants. The system treats the rename action as a success; however, the API function returns warnings that describe the failure to delete the old database or grants.

### Delete a database

To delete a database, perform the following steps:

1. In the _Current Databases_ table, click _Delete_ for the desired database.
2. To permanently delete the database, click _Delete Database_.
3. Click _Go Back_ to return to the main interface.

## Add a MySQL user

After you create a database, add users to the database and configure their privileges.

{% hint style="info" %}
Notes:

* You **must** create MySQL user accounts separately from mail and web administrator accounts.
* You **must** create a user before you can add the user to an existing database.
{% endhint %}

To create a new user account, perform the following steps:

1. Enter a username in the _Username_ text box.

   Important:

   To learn more about database username limits, click your database type: MySQL MariaDB

2. Enter and confirm the new password in the appropriate text boxes.

   Notes:

   * The system evaluates the password that you enter on a scale of 100 points. `0` indicates a weak password, while `100` indicates a very secure password.
   * Some web hosts require a minimum password strength. A green password _Strength_ meter indicates that the password is equal to or greater than the required password strength.
   * Click _Password Generator_ to generate a strong password. For more information, read our [Password & Security](https://documentation.cpanel.net/display/68Docs/Password+and+Security) documentation.

3. Click _Create User_.
4. Click _Go Back_ to return to the main interface.

## Add a user to a database

To add a user to a database, perform the following steps:

1. In the _Add User To Database_ section of the interface, select the desired user and database from the menus.
2. Click _Add_. The _MySQL Account Maintenance_ interface will appear.
3. Select the checkboxes that correspond to the privileges that you wish to grant to the user.

   Note:

   To grant all of the available privileges to the user, select the _ALL PRIVILEGES_ checkbox.

4. Click _Make Changes_.
5. Click _Go Back_ to return to the main interface.

For more information about user privileges, read the [MySQL documentation](http://dev.mysql.com/doc/).

## Current Users

The _Current Users_ table lists all of your MySQL database users, and allows you to perform the following actions:

* _Change Password_ — Click to modify a database user’s password. Enter and confirm the desired password, and then click _Change Password_.
* _Rename_ — Click to rename a database user. Enter the desired username, and then click _Change Username_.
* _Delete_ — Click to permanently delete a database user, and then click _Delete User_ to continue.

