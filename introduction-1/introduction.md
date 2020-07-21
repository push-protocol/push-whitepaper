# 1. Introduction

The blockchain space is growing at an extremely rapid pace and the exponential growth is projected to continue rapidly in terms of users, services and revenue [\[1\]](../references.md). Despite this growth and expanding usage of blockchain tech, the services \(dApps, services, smart contracts\) still lack a genuine communication medium with their users which is sometimes filled by alternative communication mediums like twitter, telegram or email defeating the purpose of web 3.0.

More often though, dApps, smart contracts or services assume that users will come to them. This method is very similar to early 2003 era of internet where users were expected to perform an action, come back later and check the results of those actions \(Gmail, Orkut, etc\). 

While this was okay with early internet days and web 2.0, It is not the case with traditional services now. In fact, no web 2.0 service really expect the user to come to them now, instead they reach out to their users informing them about certain important events or any further actions required from users end. Modern push notification played a crucial role in this transition and has become a backbone for all web 2.0 services now [\[2\]](../references.md).

However, for web 3.0, there still **doesn't exists a** **notification mechanism** that can notify users\(wallet addresses\) of important updates, events, actions, etc. This flawed mechanism has already led to pain points and side effects:

* Important events or user action requirements are missed completely \(trading completed on dEx, Liquidation alert on DeFi protocols, etc\).
* Blockchain domains expiry have to be put on twitter constant in the hopes that the grace domain user might read it.
* A protocol getting compromised means sending information through Twitter and Telegram hoping the users of that protocol become aware of the vulnerabilities.

This is a major issue in adoption and the problem will worsen more as the services keep on growing on blockchain.

This paper describes the solution to this problem and aims to provide the missing piece of web3 infrastructure with the introduction of the decentralized notification protocol. The protocol will enable users to receive notifications, be in complete control of the notifications they receive as well as enabling a passive means to earn from those notifications.

