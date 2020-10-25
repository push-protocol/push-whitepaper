# Creating Channel on dApp / Server / Smart Contract

The creation of channel is a **one time process** and as such is recommended to do it either from EPNS dApp, EPNS JS library or a custom JS library of your choice. [Information about the channel payload specs is described here](../specifications/channel-payload-specs.md).

Interfacing directly via smart contract to protocol to create a channel can also be done by calling it

*  with **public key registry** function

```text
createChannelWithFeesAndPublicKey(ChannelType _channelType, bytes calldata _identity, bytes calldata _publickey) external
```

* without **public key registry** function

```text
createChannelWithFees(ChannelType _channelType, bytes calldata _identity)
```

| Parameter | Sub Field | Description |
| :--- | :--- | :--- |
| **\_channelType** |  | The type of channel to create |
| **\_identity** |  | The identity field consists of the following parameters joined together with a delimiter. |
|  | payloadtype | Payload type not only indicates the content of notification but also the storage implementation stored. |
|  | payloadhash | Indicates the hash of the payload through which payload data can be obtained. |
| **\_publickey** |  | Pass the publickey of the wallet in bytes |

| ChannelType | Description |
| :--- | :--- |
| 0 | Non Interest Bearing, Protocol Reserved Channel for Information |
| 1 | Special Interest Bearing Protocol Reserved Opt in Channel for Promotion |
| 2 | Interest Bearing, Open Channel |
| 3 | Interest Bearing, Mutual Channel |

| payloadtype | Description |
| :--- | :--- |
| 1 | Represents storage on IPFS with letters Qm happen to correspond with the algorithm \(SHA-256\) and length \(32 bytes\) used by IPFS. |

{% hint style="info" %}
The delimiter **+** is used for joining the fields together, this is done to optimize the payload written on chain.
{% endhint %}

{% hint style="success" %}
Example **\_identity**: 1+QmXSuc8iVsNFtsqrFvgHWpa6tJXFLoq2QEWYu2aS6KF8ux
{% endhint %}

{% hint style="success" %}
Example **\_publickey**: 0x187c0568118be8032ece2499135d16a69b1da955125185c195a900d45eed0a325f2a7bf3ce6eb01375011db55d3a311fd84c2a17d0476edf8c6290f36ed2280b
{% endhint %}

{% hint style="info" %}
Always recommended to interface with **EPNS JS Library** for abstracting these details out.
{% endhint %}

{% hint style="warning" %}
This feature of protocol might change for further optimizations in the future.
{% endhint %}

