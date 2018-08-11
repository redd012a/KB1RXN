# How to create Custom Nameservers / Vanity Nameservers

We can provide custom name servers with the correct glue records associated, providing that the relevant domain is registered with Vimzaa. This is because only the domain vendor can set glue records.

If your domain is not registered with us, you would need ensure that your domain vendor sets the glue records as the following:  
  
ns1 must be set to X.X.X.X  
ns2 must be set to Y.Y.Y.Y  
  
Where X.X.X.X and Y.Y.Y.Y are the two IP addresses of the cloud that your account is on. You can find this information in your Welcome e-mail.  
  
Once the domain glue records have been set by us or your domain provider, you can then update the domain’s name server settings to use the new NS records. Finally you should ensure that A records are set within your cPanel or Plesk to point to the IP addresses of the cloud that your account is on \(as above\).  
  
Please contact us if would like assistance in achieving this by opening a support ticket.

