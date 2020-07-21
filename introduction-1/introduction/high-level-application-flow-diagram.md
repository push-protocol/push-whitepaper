# 1.2 High Level Protocol / Product Flow

![High Level Application Flow of EPNS protocol / product](../../.gitbook/assets/highleveldefi.jpg)

EPNS uses the following flow to ensure storage, broadcasting and sending notifications in a platform agnostic and decentralized way.

Notification are stored and treated like JSON payload and have types assigned to them. JSON Payload can differ with payload types ensuring flexibility of the content, data, storage interpretation and delivery. This helps in creating different rules and content interpretation of the notification. 

**The protocol lets user be in direct control of what services they get notification from, imposes rules on the services including spam protection for users, limiting their ability to add wallets as subscribers.**

**The protocol incentivizes users who receive notifications.**

This on-chain abstraction of data enables delivery to centralized as well decentralized carries as well. Storing the payload JSON on decentralized storage and just the pointer / hash of it on logs of on-chain enables cost optimization and enables decentralized carriers to trust a single source of truth.

This can be further optimized by moving parts of these mechanism to L2 layer or in the future.

{% hint style="info" %}
Abstracting the data layer on chain \(directly or indirectly\) ensures notifications are platform agnostic. 
{% endhint %}

