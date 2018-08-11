# How to flush your local machines DNS Cache

If your machine is struggling to catch up with DNS changes, then its due to the authoritative nameservers handled by your ISP \(internet service provider\) caching those records. Also, in some cases, it may be your router inside your network caching those results.

There are two solutions for this to help your machines catch up and see those changes correctly.

The first is to try…

## Flush your DNS caches

## Overview

Your DNS cache stores the locations \(IP addresses\) of web servers that contain web pages which you have recently viewed. If the location of the web server changes before the entry in your DNS cache updates, you can no longer access the site.

If you encounter a large number of [HTML 404 error codes](https://documentation.cpanel.net/display/CKB/How+To+Clear+Your+DNS+Cache#), you may need to clear your DNS cache. After you clear your DNS cache, your computer will query nameservers for the new DNS information.

## How to clear your DNS cache

The following methods allow you to remove old and inaccurate DNS information that may result in 404 errors.

### Windows® 8

To clear your DNS cache if you use Windows 8, perform the following steps:

1. On your keyboard, press **Win+X** to open the _WinX Menu_.
2. Right-click _Command Prompt_ and select _Run as Administrator_.
3. Run the following command:

   | `ipconfig /flushdns` |
   | :--- |


   If the command succeeds, the system returns the following message:

   | `Windows IP configuration successfully flushed the DNS Resolver Cache.` |
   | :--- |

### Windows® 7

To clear your DNS cache if you use Windows 7, perform the following steps:

1. Click _Start_.
2. Enter `cmd` in the _Start_ menu search text box.
3. Right-click _Command Prompt_ and select _Run as Administrator_.
4. Run the following command:

   | `ipconfig /flushdns` |
   | :--- |


   If the command succeeds, the system returns the following message:

   | `Windows IP configuration successfully flushed the DNS Resolver Cache.` |
   | :--- |

### Windows XP®, 2000, or Vista®

To clear your DNS cache if you use Windows XP, 2000, or Vista, perform the following steps:

1. Click _Start_.
2. On the _Start_ menu, click _Run…_.
   * If you do not see the _Run_ command in Vista, enter `run` in the _Search_ bar.
3. Run the following command in the _Run_ text box:

   | `ipconfig /flushdns` |
   | :--- |


   If the command succeeds, the system returns the following message:

   | `Successfully flushed the DNS Resolver Cache.` |
   | :--- |

### MacOS® 10.10.4 and above

To clear your DNS cache if you use MacOS X version 10.10.4 or above, perform the following steps:

1. Click _Applications_.
2. Click _Utilities_.
3. Click _Terminal_.
4. Run the following command:

   | `sudo` `killall -HUP mDNSResponder` |
   | :--- |


   If the command succeeds, the system does **not** return any output.

   Warning:

   To run this command, you **must** know the computer’s administrator account password.

### MacOS 10.10.1, 10.10.2, and 10.10.3

To clear your DNS cache if you use MacOS X version 10.10 through 10.10.3, perform the following steps:

1. Click _Applications_.
2. Click _Utilities_.
3. Click _Terminal_.
4. Run the following command:

   | `sudo` `discoveryutil mdnsflushcache` |
   | :--- |


   If the command succeeds, the system does **not** return any output.

   Warning:

   To run this command, you **must** know the computer’s administrator account password.

### MacOS 10.7, 10.8, and 10.9

To clear your DNS cache if you use MacOS X version 10.7, 10.8, or 10.9, perform the following steps:

1. Click _Applications_.
2. Click _Utilities_.
3. Double-click _Terminal_.
4. Run the following command:

   | `sudo` `killall -HUP mDNSResponder` |
   | :--- |


   If the command succeeds, the system does **not** return any output.

   Warning:

   To run this command, you **must** know the computer’s administrator account password.

### MacOS 10.5 and 10.6

To clear your DNS cache if you use MacOS X version 10.5 or 10.6, perform the following steps:

1. Click _Applications_.
2. Click _Utilities_.
3. Double-click _Terminal_.
4. Run the following command:

   | `sudo` `dscacheutil -flushcache` |
   | :--- |


   If the command succeeds, the system does **not** return any output.

   Warning:

   To run this command, you **must** know the computer’s administrator account password.

The other option is to use the ‘Google Public DNS’ service, which is completely free and improves DNS lookup times drastically.

