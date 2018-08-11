# How to add and manage cron jobs / scheduled tasks in cPanel

#### Location under cPanel

```text
Home > Advanced > Cron Jobs
```

### Overview {#CronJobs-Overview}

Cron jobs are scheduled tasks that the system runs at predefined times or intervals. Typically, a cron job contains a series of simple tasks that the system runs from a script file.

Notes:

Exercise caution when you schedule cron jobs. If you schedule them to run too often, they may degrade performance.

### Add a cron email {#CronJobs-Addacronemail}

The `Cron Email` section of the interface allows you to enter an email address for the system to send notifications when your cron jobs run. To set an email address, perform the following steps:

1. In the `Email`  text box, enter the email address at which you wish to receive the notifications.
2. Click `Update Email`.

#### Disable email notifications {#CronJobs-Disableemailnotifications}

To disable email notifications for all cron jobs, remove the email address.

To disable email notifications for a single cron job, perform the following steps:

1. Locate the following string:

   | `0 * * * * /home/user/backup.pl` |
   | :--- |

2. Add the following string to that line:

   | `/dev/null 2>&1` |
   | :--- |

3. Save your changes.

### Add a cron job {#CronJobs-Addacronjob}

To create a cron job, perform the following steps:

1. Select the interval at which you wish to run the cron job from the appropriate menus, or enter the values in the text boxes.
   * _Common Settings_ — This menu allows you to select a commonly-used interval. The system will configure the appropriate settings in the _Minute_, _Hour_, _Day_, _Month_, and _Weekday_ text boxes for you.

     Note:

     If the wildcard characters \(`*`\) and intervals confuse you, this menu is an excellent way to learn how to configure the other fields.

   * _Minute_ — Use this menu to select the number of minutes between each time the cron job runs, or the minute of each hour on which you wish to run the cron job.
   * _Hour_ — Use this menu to select the number of hours between each time the cron job runs, or the hour of each day on which you wish to run the cron job.
   * _Day_ — Use this menu to select the number of days between each time the cron job runs, or the day of the month on which you wish to run the cron job.
   * _Month_ — Use this menu to select the number of months between each time the cron job runs, or the month of the year in which you wish to run the cron job.
   * _Weekday_ — Use this menu to select the days of the week on which you wish to run the cron job.
2. In the _Command_ text box, enter the command that you wish the system to run.

   Note:

   Specify the absolute path to the command that you wish to run. For example, if you wish to run the `public_html/index.php` file in your home directory, enter the following command:

   | `/home/user/public_html/index.php` |
   | :--- |


   Important:

   * You **must** specify settings for the _Minute_, _Hour_, _Day_, _Month_, _Weekday_, and _Command_ text boxes.
   * Exercise **extreme** caution when you use the `rm` command in a cron job. If you do not declare the correct options, you may delete your home directory’s data.

3. Click _Add New Cron Job_.

### View existing cron jobs {#CronJobs-Viewexistingcronjobs}

The _Current Cron Jobs_ table displays your existing cron jobs.

#### Edit a cron job {#CronJobs-Editacronjob}

To edit a cron job, perform the following steps:

1. Locate the cron job that you wish to edit and click _Edit_.
2. Edit the settings that you wish to change and click _Edit Line_.

#### Delete a cron job {#CronJobs-Deleteacronjob}

To delete a cron job, perform the following steps:

1. Click _Delete_ next to the cron job that you wish to delete.
2. Click _Delete_.

