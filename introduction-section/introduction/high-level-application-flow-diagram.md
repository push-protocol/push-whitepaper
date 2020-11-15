# Protocol / Product Flow

EPNS uses the following flow to ensure storage, broadcasting and sending notifications in a platform agnostic and decentralized way.

![High level flow](../../.gitbook/assets/highleveldefi%20%281%29.jpg)

Notification is stored and treated like JSON payload which is transformed as per the rules of the different carriers when the notification reaches them. JSON Payload can differ with payload types which ensures the flexibility of the content, data, storage interpretation and delivery. This helps in creating different rules and content interpretation of the notification \(for example: carrying images, call to action, live videos, etc\).

**The protocol allows users be in direct control of what services they get notification from; it imposes rules on the services including spam protection for users, limiting their ability to add wallets as subscribers, etc.**

**The protocol incentivizes users who receive notifications.**

**This on-chain abstraction of data enables delivery of information to centralized as well decentralized carriers, notifications are treated more like a social feed \(e.g. Twitter\) than an ephemeral piece of information \(though means to do so also exists\).** 

It also enables rules, incentives, settings and configuration to be retrieved from a single source of truth and is not dependent on a single point of failure.

Storing the JSON payload on decentralized storage and just it's pointer / hash on on-chain logs enables cost optimization. Though the protocol also allows storing the entire payload on-chain for services that intend to do so.

This can be further optimized by moving parts of these mechanisms to the layer-2 \(L2\).

{% hint style="info" %}
Abstracting the data layer on chain \(directly or indirectly\) ensures notifications are platform agnostic and available on decentralized mediums as well \(e.g. dApp, wallets that might not want to trust a central point of truth\).
{% endhint %}

