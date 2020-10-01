# Special Channels

There are two special channels in the protocol that are owned and controlled by the contract owner. These channels are special because:

* They don't give any token incentives to their subscribers.
* They are the only automated opt-in channels in the protocol that doesn't pay subscribers \(yet add them without their direct consent\).

## EPNS Channel

This channel is an auto subscribe channel for all the users of the protocol. The purpose of the channel is to send out extremely important events or alerts to the subscribers. While an auto subscribe, the channel can be unsubscribed by the user and like all the other channels will lose permission to add that user again indirectly.

## EPNS Alerter Channel

The channel is an auto subscribe channel for all the other channels of the protocol. The purpose of this channel is to send out updates, alerts to other channels of the protocol. While an auto subscribe, the channel can be unsubscribed by the user and like all the other channels will lose permission to add that user again indirectly.

