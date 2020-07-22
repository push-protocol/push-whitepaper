# Notification Payload Specs

Each notification sent to the protocol is essentially a JSON payload, bytes data or hash / pointer of the JSON payload. The protocol distinguishes payloads content and the storage medium it is on by assigning payload types to each notification.

{% hint style="info" %}
The JSON Payload can differ with payload types ensuring flexibility of the content, data, storage interpretation and delivery.
{% endhint %}

## Notification JSON Payload

| Parameter | Description |
| :--- | :--- |
| **notification**  | \[Required\] Represents the notification typically delivered on the home screen of the platform \(mobile, tablet, web, etc\), the icon of the channel is automatically added to outline where the notification is coming from. |
| title | \[Required\] The title of the message displayed on the screen, this differs from the **data json** because the title while transforming the payload can be different than the title presented. For example, secret notification title are always transformed to say **Channel has sent you a secret notification.** |
| body | \[Required\] The body of the message displayed on the screen, this differs from the **data json** because the title while transforming the payload can be different than the title presented. For example, secret notification body are always transformed to say **Please open the dApp / app to view your notification.** |
| **data** | \[Optional\] The data field present here forms the visual **feedBox** for the user. Indicates the data field the payload will carry. This allows the notification to transform according to the payload type and the content defined on the platform frontend \(ie: app, dApp, wallet, etc\).  |
| type | \[Required\] Each payload has a type which tells how the data should be interpreted, this type is mirrored on the protocol function call as well.  |
| secret | \[Optional\] is required for certain payload types to decrypt the data. |
| asub | \[Optional\] is the subject shown in the feed item. |
| amsg | \[Optional\] is the message shown in the feed item, has rich text formatting. |
| acta | \[Optional\] is the call to action of that feed item. |
| aimg | \[Optional\] is the image shown in the feed item, this field is also capable of carrying **other media** links. |
| atime | \[Optional\] time in epoch when the notification should be displayed, if present, the frontend should respect this field and delay the notification till the schedule is reached. If the time is before the current time, the notification is treated as to be dispatched and displayed immediately. |
| **recipients** | \[Optional\] When present with appropriate payload type allows notification to delivered to many subscribers \(but not all subscriber\) of that channel. |

{% hint style="info" %}
If no **data** is carried in the **payload** \(or only **atime** is carried\), it is assumed that the notification is not important and hence **persist \(or appearance\)** in the frontend **feedBox** of the user.
{% endhint %}

## Payload Types

The following are few payload types which are already defined, though they can change as we move forward. Notification payload type for EPNS is infinitely extensible and opens a huge range of possibilities including **multi-factor authentication, payments, blacklisting address \(Multi-sig contract as channel with exchanges as their subscribers\), etc**, The data defined in the JSON payload they carry is used to interpret and extend that functionality.

### Direct Protocol Payload \(Type 0\)

Direct payload are special payloads meant for sending directly to protocol, the delimiter **+** divides the subject and message which are the only two fields it carries. 

```text
type+title+body
```

{% hint style="warning" %}
It's always recommended to use other payloads for dApp or server interaction. This payload should be used sparingly when it's absolutely necessary. the type here is a special field which is different from the type in identity.
{% endhint %}

{% hint style="info" %}
Always recommended to interface with **EPNS JS Library** for abstracting these details out.
{% endhint %}

### Broadcast Payload \(Type 1\)

Broadcast notification goes to all subscriber of a channel, the notification payload in this case is not encrypted.

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "1",
    "secret": "",
    "asub": "[Optional] The subject of the message displayed inside app (80 Chars)",
    "amsg": "[Optional] The intended message displayed inside app (500 Chars)",
    "acta": "[Optional] The cta link parsed inside the app",
    "aimg": "[Optional] The image url or youtube url which is shown inside the app",
    "atime": "[Optional] Epoch time for the notification to be shown or dispatch"
  }
}
```

### Secret Payload \(Type 2\)

Secret notifications are intended to be delivered to one subscriber of the channel, these are encrypted using ECC\(Elliptic Curve Cryptography\) [`[4]`](../../references.md) and AES\(Advanced Encryption Standard\) [`[5]`](../../references.md). The secret which is generated by the channel using whatever means they prefer should be kept to 15 characters or less, this secret \(plain version\) uses AES to encrypt the fields: **asub, amsg, acta, aimg**.

The rationale behind using ECIES with AES is to ensure that the payload is not over bloated.

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "2",
    "secret": "No more than 15 characters, encrypted using public key of the intended recipient",
    "asub": "encrypted by secret using AES | [Optional] The subject of the message displayed inside app (80 Chars)",
    "amsg": "encrypted by secret using AES | [Optional] The intended message displayed inside app (500 Chars)",
    "acta": "encrypted by secret using AES | [Optional] The cta link parsed inside the app",
    "aimg": "encrypted by secret using AES | [Optional] The image url which is shown inside the app",
    "atime": "[Optional] Epoch time for the notification"
  }
}
```

{% hint style="info" %}
Why not just use ECIES? ECIES increases the length of the cipher text and hence the payload which will be delivered. Using ECIES with AES ensure the payload length is kept at a manageable level and allows channels to send more information in the notification while still keeping the best encryption practices.
{% endhint %}

{% hint style="warning" %}
The discussion on using a public key - private key encryption or a derivation of it is still in discussion. Even if we decide to go with the above encryption for secret messages. We can in the future also create a payload type that can offer encryption / decryption in a different way.
{% endhint %}

#### Example Notification Payload \(Plain\)

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "2",
    "secret": "vBGK71PFl7mzWob",
    "asub": "The Great Renewal: Your ENS Domain has expired and someone is about to get them",
    "amsg": "[d:ENS] domains from 2017 that have expired.\n\nGo check your [b:@ensdomains] right now and renew your accounts.",
    "acta": "https://ens.domains/",
    "aimg": "https://i.ibb.co/WKNVN9y/enssamplemsgimg.jpg",
    "atime": "1595083821"
  }
}
```

{% hint style="info" %}
**Recommended** to use the **EPNS** **JS Library** to handle the generation of encrypted payload easily, it can talk to our protocol to also fetch the public key required.
{% endhint %}

#### Example Notification Payload \(Encrypted\)

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "2",
    "secret": "e291826a995ab03b0dd69c360f3deb3803e130dc7d3bd94f1016494bc1fad4f4b816524f8cbdd068f0caf94a1cec682ab75755327e4410267721e44f83d73a56e88b911051eb0a2f2ee1ffef5f2cf5419cbc81895cd7d290b70060ef80b727fd52",
    "asub": "U2FsdGVkX181J09umWprAgmLOaDyZXojQjLPlJ31G0LDgXHBgnNsFEOKgjqhKJ2vWaPP5Xmt8sIQLmB3YYkjQO1LhrV7sr0FDlwqjLhSimxmI1EnjOdEHyiE1RO7LV0O",
    "amsg": "U2FsdGVkX18J7Myet9yljBLtNMpqz86qWgmjrK/9WyP+LD9OVerohkl5jc791UOlU6cV4UFVhdwJHyQSMYNNDPOaJMhxlLF2tL7LIBDeGqPA2AlgWqe2qbF1JC+zjIgBR/+IUfbr0+gz4JUBydK3d1dJGPFYliQTqD7EOjv38No=",
    "acta": "U2FsdGVkX188zXRR3URQR2xedjftDOHD5E3k+ggKe+8F6MxW86464rl6y1ZhX3jY",
    "aimg": "U2FsdGVkX188AaU187LFzqaibpfoOXb+XkCNbsLpV29CrQOVjC9BfWpxwGXE9Er7OdJ63yblqFYCaqNoGAHCOg==",
    "atime": "1595083821"
  }
}
```

### Targeted Payload \(Type 3\)

Targeted notification goes to a single subscriber of a channel, the notification payload in this case is not encrypted.

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "3",
    "secret": "",
    "asub": "[Optional] The subject of the message displayed inside app (80 Chars)",
    "amsg": "[Optional] The intended message displayed inside app (500 Chars)",
    "acta": "[Optional] The cta link parsed inside the app",
    "aimg": "[Optional] The image url or youtube url which is shown inside the app",
    "atime": "[Optional] Epoch time for the notification to be shown or dispatch"
  }
}
```

## Extending for Future Payload 

{% hint style="info" %}
The following payloads are in discussion and form an example of how the payload specs is ever expanding and can include more than just information as notification.
{% endhint %}

### Multi-Targeted Payload \(Type x\)

Multi-Targeted notification goes to a more than one subscriber of a channel, the notification payload in this case is not encrypted. The total number of subscribers supported is TBA.

```text
{
  "notification": {
    "title": "The title of your message displayed on screen (50 Chars)",
    "body": "The intended message displayed on screen (180 Chars)"
  },
  "data": {
    "type": "4",
    "secret": "",
    "asub": "[Optional] The subject of the message displayed inside app (80 Chars)",
    "amsg": "[Optional] The intended message displayed inside app (500 Chars)",
    "acta": "[Optional] The cta link parsed inside the app",
    "aimg": "[Optional] The image url or youtube url which is shown inside the app",
    "atime": "[Optional] Epoch time for the notification to be shown or dispatch"
  },
  "recipients": {
    [0xAb...],
    ...
    [0xEb...]
  }
}
```

### Blacklist Payload \(Type x\)

Blacklist payload are a future forward payload meant to only demonstrate how the payload data and type defines what information the payload will carry.

```text
{
  "data": {
    "type": "5",
    "blacklist": {
      address1,
      address2,
      ....
      address100
    }
  }
}
```

{% hint style="info" %}
The support for payload types is left to the third party frontend / infrastructure services to implement. The accompanying EPNS products however will implement all payloads types which are accepted as official after community discussion.
{% endhint %}

