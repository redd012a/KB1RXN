# Understanding Subscriptions in Plesk

To understand how the usage of resources is managed in Plesk, as well as how the number of options available to different users is controlled, you need to learn about the concept of _subscription_.

When a customer purchases a hosting account, a _subscription_ is created in Plesk for them. A subscription can be defined as a combination of resources available and permissions granted to a user. Resources include disk space and traffic, and permissions include, for example, the ability to add additional domains or change PHP settings. Permissions give providers a lot of flexibility regarding whether or not customers are allowed to manage certain services and perform certain operations.

**Note:** Later in this guide, you will find instructions explaining how to perform a wide variety of everyday tasks. If you are unable to follow a set of instructions because of a missing tab or button, the most likely cause is that the provider has disabled the corresponding permission in your subscription’s properties. Contact your provider for assistance.

Resources assigned to a subscription can be used however the customer sees fit. For example, if a subscription includes 100 megabytes of disk space, the customer is free to use the disk space for domain content, mail, databases, or all of these. If the subscription allows multiple domains to be created, the customer can create one or more additional domains and split the available disk space among them.

A single customer can own more than one subscription. It is important to understand that in such cases resources are not shared between subscriptions. For example, if a customer has two subscriptions, both of which include 100 megabytes of disk space, the customer cannot use 150 megabytes for one subscription and 50 for the other. Such resource usage is in violation of one of the subscriptions’ resource limits and may cause the offending subscription to be suspended.

**Caution:** If a subscription is suspended, all domains associated with it become unavailable and the owner is unable to manage the subscription until it has been activated by the provider. If you find that your subscription is suspended, contact your provider as soon as possible to resolve the issue.

If you are managing your own Plesk server and are hosting your own websites, or those of your customers, there is no need for resource limits, so your subscription has unlimited resources

