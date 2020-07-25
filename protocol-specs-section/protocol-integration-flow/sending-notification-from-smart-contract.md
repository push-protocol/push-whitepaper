# Sending Notification from Smart Contract

## Smart Contract workflow 

EPNS allows various ways to integrate the protocol into your service. The following flow shows how your server can integrate and send notification to the protocol.

![](../../.gitbook/assets/inputsmartcontract.png)

## Sending notification via the smart contract

1. Use your internal logic to figure out what notification you want to send \(i.e. alerting users on some smart contract event, user actions, etc\).
2. This can be done by either having internal logic cooked in your protocol or better yet having a function which you can call from outside which can interact with our protocol.
3. Please check for supported payload types and their requirements.
4. Either pass the hash of the content or the data in bytes to EPNS protocol.

