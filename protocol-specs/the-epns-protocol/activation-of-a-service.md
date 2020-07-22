# Activating a Channel

### Concept

A **service** needs to activate themselves on the protocol as a one time step before they can send notification to their subscribers. When a service is activated on the protocol, they are referred to as a **Channel**.

The channel is also required to stake fees in DAI which is **50 DAI or higher**, this is used to create a staking pool which in turn interacts with other DeFi protocol to earn interest. This interest is then distributed to all the **subscribers** of that service in a weighted manner preferring the earliest subscriber more than the later ones.

{% hint style="info" %}
There is always 1:1 mapping between a service \(wallet\) and the channel it creates.
{% endhint %}

### Game Theory

Any service needs to activate itself as a channel before they can send notification via the protocol. Game Theory is utilized 

The protocol requires a service to activate themselves by creating a **channel** , The activation requires them staking 50 DAI \(at the time of writing\) or higher on the protocol, which is then deposited in a interest generating protocol \(AAVE at the time of writing\), which in turn is shared by all the subscribers of the service as a reward. 

The protocol attaches weights and indexes to all the services and subscribers in order to distribute the interest earned in a weighted manner among the subscribers, the weight always prefers the earliest block number or the earliest subscriber \(ie: user who subscribe of block 1 will earn more than the subscriber of block 10\).

