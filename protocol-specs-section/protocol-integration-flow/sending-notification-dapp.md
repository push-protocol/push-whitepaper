# Sending Notification from dApp / Serverless

## dApp / Serverless integration workflow

EPNS allows various ways to integrate the protocol into your service. The following flow shows how a dApp can send notifications to the protocol.

![](../../.gitbook/assets/inputdappserverless.png)

## Sending notification via the dApp

1. Use your internal logic to figure out what notification you want to send \(i.e. alerting users on some smart contract event, user actions, movement in their wallets, a podcast or post from your end, etc\).
2. Form the JSON payload using our JS Library or your which you want to send as notification. Please check supported payload types and their requirements.
3. Interact with protocol using EPNS JS Library.

