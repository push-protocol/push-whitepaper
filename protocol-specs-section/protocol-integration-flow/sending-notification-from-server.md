# Sending Notification from Server

## Server integration workflow

Push allows various ways to integrate the protocol into your service. The following flow shows how your server can integrate and send notification to the protocol.

![](../../.gitbook/assets/inputserver.png)

## Sending notification via the server

1. Use your internal logic to figure out what notification you want to send \(i.e. alerting users on some smart contract event, user actions, movement in their wallets, a podcast or post from your end, etc\).
2. Form the JSON payload using our JS Library or your which you want to send as notification. Please check supported payload types and their requirements.
3. Interact with protocol using Push JS Library.

