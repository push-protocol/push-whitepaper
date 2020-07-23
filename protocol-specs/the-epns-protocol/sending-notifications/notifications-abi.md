# Protocol Interfacing for Notifications

## Concept

All of the payloads are uploaded as JSON format in decentralized storage solutions \(**or in some special future cases, even centralized ones**\). The EPNS JS Library interfaces with Ethereum Push Notification Service protocol and calls:

```text
sendNotification(address _recipient, bytes _identity)
```

| Parameter | Sub Field | Description |
| :--- | :--- | :--- |
| **\_recipient** |  | Differs with the payload type, broadcast and special multi payload notifications have the channel address as the recipient address. |
| **\_identity** |  | The identity field consists of the following parameters joined together with a delimiter. |
|  | provider | The provider to which the notification fee will go to when it comes to using push notifications or using centralized carriers. |
|  | pushtype | Indicates service wants to push the notifications out and can in the future be segmented to different platforms push \(i.e. : 1 for every platform, 2 for mobile, 3 for web browsers, etc\). |
|  | payloadtype | Indicates the payload type which is getting written on chain |
|  | payloadhash | Indicates the hash of the payload through which payload data can be obtained, payload type not only indicates the content of notification but also the storage implementation stored. |

{% hint style="info" %}
The delimiter **+** is used for joining the fields together, this is done to optimize the payload written on chain.
{% endhint %}

{% hint style="success" %}
Example identity: **1+1+2+QmcdzjicUnxv8ASKKSgEEYjhK7symwxqDG4BeCS82rdNBk**
{% endhint %}

{% hint style="info" %}
Always recommended to interface with **EPNS JS Library** for abstracting these details out.
{% endhint %}

{% hint style="warning" %}
This feature of protocol will keep on changing for further optimizations in the future.
{% endhint %}

