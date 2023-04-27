# Channel Activation & Deactivation

## Concept

A **service** needs to activate itself on the protocol as a one time step before they can send notifications to their subscribers. When a service is activated on the protocol, they are referred to as a **Channel**.

The channel is also required to stake fees in DAI which is **50 $PUSH or higher**, this is used to create a staking pool which in turn interacts with other DeFi protocols to receive token incentives. These token incentives are then distributed to all the **subscribers** of that service in a weighted manner preferring the earliest subscriber more than the later ones.

{% hint style="info" %}
There is always 1:1 mapping between a service \(wallet\) and the channel it creates.
{% endhint %}

## Game Theory and User Incentives

In order to ensure the proper participation of all ecosystem users, following game theory is applied to keep each user in the system motivated to be a good actor in the ecosystem.

* Contract owner cannot send notification on behalf of channel unless the control is delegated to it by the channel owner as an on-chain event.
* The **service** needs to deposit **50 $PUSH or higher** as staking fee to activate themselves, this ensures that serious users participate in the channel creation.
* The **channel stake** goes to a combined stake pool of channels and starts accumulating token incentives using [**AAVE Protocol**](https://aave.com/) ****\(at the time of writing, this can be replaced with a similar DeFi protocol in the future\).
* The **channel owner** will be able to decide on the level of channel stake it is willing to put up, since eventually all token incentives attributable to this channel stake will be distributed among their users weighted towards the earliest subscriber, and is refundable, having **higher stake incentivizes more users** to subscribe to the channel.
* This **channel** can be deactivated by the **channel owner** with a penalty of **20 $PUSH**, this ensures that bad actors are unable to abuse the system as a monetary loss will occur with each recurrence, small enough for serious users to not worry about it but act as a further deterrent for malicious users.
* Upon deactivation, the channel is unable to send notification and its ratio in the **stake pool** is reduced to **10 $PUSH**, as a result, the proportionate ratio from token incentives pool for the channel is also reduced accordingly. The channel continues distributing its fair share of token incentives to all existing subscribers of the channel, though the channel loses the ability to add more users.
* The rest of the penalty \(**10 $PUSH**\) goes into the Fee Pool.

{% hint style="info" %}
There is an upper ceiling limit applied for staking fee to ensure that a service is not approving an unlimited amount of fees to transfer \(250k DAI at the time of writing\). This is mostly to avoid the mentioned problem and should not really be effecting any features or UX of the protocol.
{% endhint %}

{% hint style="info" %}
The penalty fee, stake fee can be adjusted in the future before going to the mainnet. After mainnet, it can only be adjusted by voting mechanism of the protocol.
{% endhint %}



