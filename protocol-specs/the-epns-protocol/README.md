# 2. The EPNS Protocol

Ethereum Push Notification Service \(EPNS\) is a protocol on the Ethereum blockchain that provides and standardizes the ways by which notification on blockchain can operate. They also need to be decentralized, be able to adapt future changes of payload, be flexible to handle different content and should contain measures which are user centric and incentivizes the users for receiving notifications besides offering them measures for spam protection.

The features of the protocol can be categorized as the following features: 

* Activation of a service as a Channel
* Users subscribing channels to receive notifications
* Incentivizing users on subscription \(direct action or when a channel adds them indirectly\)
* Spam protection for users
* Unsolicited notification protection for users
* Flexible notification payload \(enhance flexibility of the content, data, storage interpretation and delivery\)
* Sending notification to the users
* Future features

At its' heart, the protocol requires a service to activate themselves by creating a **channel** , The activation requires them staking 50 DAI \(at the time of writing\) or higher on the protocol, which is then deposited in a interest generating protocol \(AAVE at the time of writing\), which in turn is shared by all the subscribers of the service as a reward. 

The protocol attaches weights and indexes to all the services and subscribers in order to distribute the interest earned in a weighted manner among the subscribers, the weight always prefers the earliest block number or the earliest subscriber \(ie: user who subscribe of block 1 will earn more than the subscriber of block 10\).









