# Indirect subscribe action \(delegate subscription of user by channel\)

## Concept

The indirect subscribe action provides channels a way to subscribe users and thus send notification to them without the explicit permission of the user. While this action is obtrusive in nature and opens up the protocol for misuse, we do however also see it's use cases:

* When channel doesn't have any means to reach the user
* When user is not added in the protocol or the channel but notification is important \(example: ENS domain expiry or security compromise\)
* For closed channels and their business use case \(For example: Notification that does multi factor authentication should not be open for any action of the user\)

Seeing this as a necessity, we do have provisions in the protocol to initiate subscribe from a channel to a user. Since, this action has larger consequences on the user if misused, we have set the following rules and higher incentives for indirect subscribe action.

## Game Theory and User Incentives

The indirect subscribe action imposes the following rules and conditions on the channel:

* The indirect subscribe can only occur once, if the user unsubscribes, there is no way to add them back.
* The user can set and change at will their fees which a channel needs to pay to them for indirect subscribe.
* The channel needs to pay user the above specified amount and only then can the indirect subscribe occur, this directly goes to the earning reserve of the user. 
* If the user hasn't set an indirect fees amount yet, then a default amount **0.1 DAI** still needs to be paid before an indirect subscribe can occur.

{% hint style="info" %}
The indirect fees can be adjusted in the future before going to the mainnet. After mainnet, it can only be adjusted by voting mechanism of the protocol.
{% endhint %}

