# Users Registry

## Concept

The users registry is maintained in the protocol to carry out various tasks such as stopping channels from adding them again \(after a user has unsubscribed\), if their public key is in the registry, what channels they are subscribed to and a mapping to get to those channels, if they own a channel, etc.

## Key data stored on chain 

* If the user is already in the ecosystem
* If their public key is already in the registry
* Whether they own a channel
* The channels they have subscribed to
* The channels they have graylisted

