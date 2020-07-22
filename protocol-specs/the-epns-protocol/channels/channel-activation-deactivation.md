# Channel Activation & Deactivation

## Concept

A **service** needs to activate themselves on the protocol as a one time step before they can send notification to their subscribers. When a service is activated on the protocol, they are referred to as a **Channel**.

The channel is also required to stake fees in DAI which is **50 DAI or higher**, this is used to create a staking pool which in turn interacts with other DeFi protocol to earn interest. This interest is then distributed to all the **subscribers** of that service in a weighted manner preferring the earliest subscriber more than the later ones.

{% hint style="info" %}
There is always 1:1 mapping between a service \(wallet\) and the channel it creates.
{% endhint %}

## Game Theory and User Incentives

In order to ensure the proper participation of all players, following game theory is applied to keep each player in the system motivated to be a good actor in the ecosystem.

* Contract owner cannot send notification on behalf of channel unless the control is delegated to it by the channel owner as an on-chain event.
* The **service** needs to deposit **50 DAI or higher** as staking to activate themselves, this ensures that serious players participate in the game.
* The **channel stake** goes to a combined stake pool of channels and starts earning interest using [**AAVE Protocol**](https://aave.com/) ****\(at the time of writing, this can be replaced with a similar DeFi protocol in the future\).
* The **channel owner** decides the fees, since this interest is distributed among their users weighted towards earliest subscriber, and is refundable, having **higher stake incentivizes more users** to subscribe to the channel.
* This **channel** can be deactivated by the **channel owner** with a penalty of **20 DAI**, this ensures that bad actors are unable to abuse the system as monetary loss will occur with each recurrence, small enough for serious players to not worry about it but act as a further deterrent for bad players.
* Upon deactivation, the channel is unable to send notification and his ratio in the **stake pool** is reduced to **10 DAI**, as a result, the proportionate ratio from interest pool for the channel is also reduced according, the channel continues giving its' fair share of interest to all existing subscribers of the channel, though the channel loses the ability to add more users.
* The rest of the penalty \(**10 DAI**\) goes into the revenue pool.

{% hint style="info" %}
The penalty fee, stake fee can be adjusted in the future in a decentralized manner
{% endhint %}

