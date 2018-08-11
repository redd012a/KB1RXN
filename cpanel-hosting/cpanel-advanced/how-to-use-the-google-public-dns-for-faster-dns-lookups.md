# How to use the Google Public DNS for faster DNS lookups

When you use Google Public DNS, you are changing your DNS “switchboard” operator from your ISP to Google Public DNS.

In most cases, the IP addresses used by your ISP’s domain name servers are automatically set by your ISP via the Dynamic Host Configuration Protocol \(DHCP\). To use Google Public DNS, you need to explicitly change the DNS settings in your operating system or device to use the Google Public DNS IP addresses. The procedure for changing your DNS settings varies according to operating system and version \(Windows, Mac or Linux\) or the device \(computer, phone, or router\). We give general procedures here that might not apply for your OS or device; please consult your vendor documentation for authoritative information.**Caution:** We recommend that only users who are proficient with configuring operating system settings make these changes.

## Important: Before you start

Before you change your DNS settings to use Google Public DNS, be sure to write down the current server addresses or settings on a piece of paper. It is very important that you keep these numbers for backup purposes, in case you need to revert to them at any time.

We also recommend that you print this page, in the event that you encounter a problem and need to refer to these instructions.

## Google Public DNS IP addresses

The Google Public DNS IP addresses \(IPv4\) are as follows:

* 8.8.8.8
* 8.8.4.4

The Google Public DNS IPv6 addresses are as follows:

* 2001:4860:4860::8888
* 2001:4860:4860::8844

You can use either address as your primary or secondary DNS server. You can specify both addresses, but do not specify the same address as both primary and secondary.

You can configure Google Public DNS addresses for either IPv4 or IPv6 connections, or both. For IPv6-only networks with a NAT64 gateway using the `64:ff9b::/96` prefix, you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) instead of Google Public DNS IPv6 addresses, providing connectivity to IPv4-only services without any other configuration.

Some devices use separate fields for all eight parts of IPv6 addresses and cannot accept the `::` IPv6 abbreviation syntax. For such fields enter:

* 2001:4860:4860:0:0:0:0:8888
* 2001:4860:4860:0:0:0:0:8844

Expand the `0` entries to `0000` if four hex digits are required.

## Change your DNS servers settings

Because the instructions differ between different versions/releases of each operating system, we only give one version as an example. If you need specific instructions for your operating system/version, please consult your vendor’s documentation. You may also find answers on our [user group](https://groups.google.com/group/public-dns-discuss?hl=en).

Many systems allow you to specify multiple DNS servers, to be contacted in a priority order. In the following instructions, we provide steps to specify only the Google Public DNS servers as the primary and secondary servers, to ensure that your setup will correctly use Google Public DNS in all cases.**Note:** Depending on your network setup, you may need administrator/root privileges to change these settings.

### Windows

DNS settings are specified in the **TCP/IP Properties** window for the selected network connection.

**Example: Changing DNS server settings on Windows 7**

1. Go to the **Control Panel**.
2. Click **Network and Internet** &gt; **Network and Sharing Center** &gt; **Change adapter settings**.
3. Select the connection for which you want to configure Google Public DNS. For example:

   * To change the settings for an Ethernet connection, right-click **Local Area Connection** &gt; **Properties**.
   * To change the settings for a wireless connection, right-click **Wireless Network Connection** &gt; **Properties**.

   If you are prompted for an administrator password or confirmation, type the password or provide confirmation.

4. Select the **Networking** tab. Under **This connection uses the following items**, select **Internet Protocol Version 4 \(TCP/IPv4\)** or **Internet Protocol Version 6 \(TCP/IPv6\)** and then click **Properties**.
5. Click **Advanced** and select the **DNS** tab. If there are any DNS server IP addresses listed there, write them down for future reference, and remove them from this window.
6. Click **OK**.
7. Select **Use the following DNS server addresses**. If there are any IP addresses listed in the **Preferred DNS server** or**Alternate DNS server**, write them down for future reference.
8. Replace those addresses with the IP addresses of the Google DNS servers:
   * For IPv4: 8.8.8.8 and/or 8.8.4.4.
   * For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844.
   * For IPv6-only: you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the IPv6 addresses in the previous point.
9. Restart the connection you selected in step 3.
10. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.
11. Repeat the procedure for additional network connections you want to change.

### Mac OS

DNS settings are specified in the **Network** window.

**Example: Changing DNS server settings on Mac OS 10.5**

1. Click **Apple** &gt; **System Preferences** &gt; **Network**.
2. If the lock icon in the lower left-hand corner of the window is locked, click the icon to make changes, and when prompted to authenticate, enter your password.
3. Select the connection for which you want to configure Google Public DNS. For example:
   * To change the settings for an Ethernet connection, select **Built-In Ethernet**, and click **Advanced**.
   * To change the settings for a wireless connection, select **Airport**, and click **Advanced**.
4. Select the **DNS** tab.
5. Click **+** to replace any listed addresses with, or add, the Google IP addresses at the top of the list:
   * For IPv4: 8.8.8.8 and/or 8.8.4.4.
   * For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844.
   * For IPv6-only: you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the IPv6 addresses in the previous point.
6. Click **Apply** &gt; **OK**.
7. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.
8. Repeat the procedure for additional network connections you want to change.

### Linux

In most modern Linux distributions, DNS settings are configured through Network Manager.

**Example: Changing DNS server settings on Ubuntu**

1. Click **System** &gt; **Preferences** &gt; **Network Connections**.
2. Select the connection for which you want to configure Google Public DNS. For example:
   * To change the settings for an Ethernet connection, select the **Wired** tab, then select your network interface in the list. It is usually called `eth0`.
   * To change the settings for a wireless connection, select the **Wireless** tab, then select the appropriate wireless network.
3. Click **Edit**, and in the window that appears, select the **IPv4 Settings** or **IPv6 Settings** tab.
4. If the selected method is **Automatic \(DHCP\)**, open the dropdown and select **Automatic \(DHCP\) addresses only**instead. If the method is set to something else, do not change it.
5. In the **DNS servers** field, enter the Google Public DNS IP addresses, separated by a comma:
   * For IPv4: 8.8.8.8 and/or 8.8.4.4.
   * For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844.
   * For IPv6-only: you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the IPv6 addresses in the previous point.
6. Click **Apply** to save the change. If you are prompted for a password or confirmation, type the password or provide confirmation.
7. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.
8. Repeat the procedure for additional network connections you want to change.

If your distribution doesn’t use Network Manager, your DNS settings are specified in `/etc/resolv.conf`.

**Example: Changing DNS server settings on a Debian server**

1. Edit `/etc/resolv.conf`:

   ```text
   sudo vi /etc/resolv.conf
   ```

2. If any `nameserver` lines appear, write down the IP addresses for future reference.
3. Replace the `nameserver` lines with, or add, the following lines:

   For IPv4:

   ```text
   nameserver 8.8.8.8
   nameserver 8.8.4.4
   ```

   For IPv6:

   ```text
   nameserver 2001:4860:4860::8888
   nameserver 2001:4860:4860::8844
   ```

   For IPv6-only, you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the above IPv6 addresses.

4. Save and exit.
5. Restart any Internet clients you are using.
6. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.

Additionally, if you are using DHCP client software that overwrites the settings in `/etc/resolv.conf`, you will need to set up the client accordingly by editing the client’s configuration file.

**Example: Configuring DHCP client sofware on a Debian server**

1. Back up `/etc/resolv.conf`:

   ```text
   sudo cp /etc/resolv.conf /etc/resolv.conf.auto
   ```

2. Edit `/etc/dhcp3/dhclient.conf`:

   ```text
   sudo vi /etc/dhcp3/dhclient.conf
   ```

3. If there is a line containing `domain-name-servers`, write down the IP addresses for future reference.
4. Replace that line with, or add, the following line:

   For IPv4:

   ```text
   prepend domain-name-servers 8.8.8.8, 8.8.4.4;
   ```

   For IPv6:

   ```text
   prepend domain-name-servers 2001:4860:4860::8888, 2001:4860:4860::8844;
   ```

   For IPv6-only, you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the above IPv6 addresses.

5. Save and exit.
6. Restart any Internet clients you are using.
7. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.

### Routers

Every router uses a different user interface for configuring DNS server settings; we provide only a generic procedure below. For more information, please consult your router documentation.**Note:** Some ISPs hard-code their DNS servers into the equipment they provide; if you are using such a device, you will not be able to configure it to use Google Public DNS. Instead, you can configure each of the computers connected to the router, as described above.

To change your settings on a router:

1. In your browser, enter the IP address to access the router’s administration console.
2. When prompted, enter the password to access network settings.
3. Find the screen in which DNS server settings are specified.
4. If there are IP addresses specified in the fields for the primary and seconday DNS servers, write them down for future reference.
5. Replace those addresses with the Google IP addresses:
   * For IPv4: 8.8.8.8 and/or 8.8.4.4.
   * For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844.
   * For IPv6-only: you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the IPv6 addresses in the previous point.
6. Save and exit.
7. Restart your browser.
8. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.

Some routers use separate fields for all eight parts of IPv6 addresses and cannot accept the `::` IPv6 abbreviation syntax. For such fields enter:

* 2001:4860:4860:0:0:0:0:8888
* 2001:4860:4860:0:0:0:0:8844

Expand the `0` entries to `0000` if four hex digits are required.

### Mobile or other devices

DNS servers are typically specified under advanced Wi-Fi settings. However, as every mobile device uses a different user interface for configuring DNS server settings, we provide only a generic procedure below. For more information, please consult your mobile provider’s documentation.

To change your settings on a mobile device:

1. Go to the screen in which Wi-Fi settings are specified.
2. Find the screen in which DNS server settings are specified.
3. If there are IP addresses specified in the fields for the primary and seconday DNS servers, write them down for future reference.
4. Replace those addresses with the Google IP addresses:
   * For IPv4: 8.8.8.8 and/or 8.8.4.4.
   * For IPv6: 2001:4860:4860::8888 and/or 2001:4860:4860::8844.
   * For IPv6-only: you can use [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) _instead of_ the IPv6 addresses in the previous point.
5. Save and exit.
6. Test that your setup is working correctly; see [Test your new settings](https://developers.google.com/speed/public-dns/docs/using#testing) below.

## Test your new settings

To test that the Google DNS resolver is working:

1. From your browser, enter a hostname URL \(such as [`http://www.google.com/`](http://www.google.com/)\). If it resolves correctly, bookmark the page, and try accessing the page from the bookmark.

   * If you are using [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) on an IPv6-only system, repeat the above test with an IPv4-only hostname URL \(such as [`http://ipv4.google.com/`](http://ipv4.google.com/)\).

   If all of these tests work, everything is working correctly. If not, go to step 2.

2. From your browser, type in a fixed IP address. You can use [`http://216.218.228.119/`](http://216.218.228.119/) \(which points to the [test-ipv6.com](http://test-ipv6.com/) website\) as the URL.[1](https://developers.google.com/speed/public-dns/docs/using#footnote1)

   * If you are using [Google Public DNS64](https://developers.google.com/speed/public-dns/docs/dns64) on an IPv6-only system, use [`http://[64:ff9b::d8da:e477]/`](http://[64:ff9b::d8da:e477]/) as the URL instead. If this test does not work, you do not have access to a NAT64 gateway at the reserved prefix `64:ff9b::/96` and cannot use Google Public DNS64.
   * If you are using an IPv6-only system without Google Public DNS64, use [`http://[2001:470:1:18::119]/`](http://[2001:470:1:18::119]/) as the URL instead.

   If this works correctly, bookmark the page, and try accessing the page from the bookmark. If these tests work \(but step 1 fails\), then there is a problem with your DNS configuration; check the steps above to make sure you have configured everything correctly. If these tests do not work, go to step 3.

3. Roll back the DNS changes you made and run the tests again. If the tests still do not work, then there is a problem with your network settings; contact your ISP or network administrator for assistance.

If you encounter any problems after setting Google Public DNS as your resolver, please run the [diagnostic procedure](https://developers.google.com/speed/public-dns/docs/troubleshooting).

1 _Google thanks Jason Fesler for granting permission to use_ [_test-ipv6.com_](http://test-ipv6.com/) _URLs for browser DNS testing purposes._

## Switch back to your old DNS settings

If you had not previously configured any customized DNS servers, to switch back to your old settings, in the window in which you specified the Google IP addresses, select the option to enable obtaining DNS server addresses automatically, and/or delete the Google IP addresses. This will revert your settings to using your ISP’s default servers.

If you need to manually specify any addresses, use the procedures above to specify the old IP addresses.

If necessary, restart your system.

