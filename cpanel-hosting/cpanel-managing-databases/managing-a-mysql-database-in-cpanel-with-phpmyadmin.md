# Managing a MySQL Database in cPanel with phpMyAdmin

## Overview

While creating a database, following are some additional things that they need to organize –

* Creating a database user
* Giving your database user rights to work with your database

Fortunately, cPanel added the **MySQL Database Wizard** that can help in creation of database by following the steps below.

### **How to create database in cPanel using the MySQL Database Wizard-**

* Login to your cPanel account provided by your cPanel hosting provider
* Click the **MySQL Database Wizard** below the Databases
* Enter a name for your database next to **New Database** and click on **Next Step**
* Enter a username Next to **Username**.
* Enter a password next to **Password**, reenter the Password and then click on **Create User**
* On the next page, you can assign rights for the user to the database. Check the box next to **All Privileges**and then click on **Next Step**

 You have created the database successfully!

You can handle various options for managing the databases by using phpMyAdmin in cPanel such as:

* **Structure:**  Helps to organize your schemas, tables, and columns.
* **SQL:**  Runs SQL query/queries on a database.
* **Search:** Searches words or values inside database tables.
* **Query:** SQL defines a set of commands, such as SELECT, INSERT, UPDATE, DELETE, CREATE TABLE and etc.
* **Export:** Exports database in different formats such as CSV, PDF, SQL, XML, Text etc.
* **Import:** Imports database in different formats such as OpenDocument Spreadsheet, CSV, SQL, ESRI Shape file, MediaWiki Table, XML.
* **Operations:** There are various operations which you can execute on the whole database and on a separate table.
* **Triggers:** A trigger is known as database object that is linked with a table, and it activates whenever a particular event \(e.g. an insert, update or delete\) happens for the table.

The basic functionality of the phpMyAdmin is to manage your databases. Follw the steps  below to create database

**Step1:**

Click on the **Databases** tab. Choose the database which you want to manage and click on the database name.

![Databases-in-phpMyAdmin](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Databases-in-phpMyAdmin.png)

**Step 2:**

After clicking on the database name, you will see the list of **database tables**.

![Database-Tables](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Database-Tables.png)

## **Operations to Perform on the Database**

### **Browse**

You can only browse the database tables with existing records. The **Browse** window opens with the records when you click on the table name.

![Browse](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Browse-1024x462.png)

By simply clicking on the Pen symbol, you can edit the selected record.

### **Structure**

In the **structure** screen you will see the structure of database’s table. You will see the field name, their data types, collation, attributes etc. You can change the field’s structure as well as delete a field. Also, you can assign indexes i.e. Primary, Unique, Index, Fulltext.

![Structure](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Structure-1024x454.png)

### **Search**

You can create a search query for the selected table by using **Search** action. Either you can write the WHERE clause or use the “query by example” option. You must click on the Go button to perform search query.

![Search](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Search-1024x444.png)

### **Insert**

You can insert the records in database table through the **Insert** action. To insert a new record you need to fill the appropriate values and click on the Go button.

![Insert](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Insert.png)

### **Empty**

You can empty your database table using the **Empty** option. It will remove the records and keep the table blank.

![Empty](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Empty.png)

### **Drop**

You can delete the table as well as delete stored records in it by using the **Drop** option

![Drop](https://www.eukhost.com/kb/wp-content/uploads/2017/05/Drop.png)

