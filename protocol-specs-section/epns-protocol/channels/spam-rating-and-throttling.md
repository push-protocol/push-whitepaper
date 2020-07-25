# Spam score and throttling

The protocol uses game theory and incentives to ensure that the channel stay useful to the users. However, there might come a point where a channel might become a bad actor despite the incentives and penalty imposed. This can happen in various scenarios, a couple of them can be:

* Popular channel is bought by someone else with the purpose to promote advertisements.
* Channel private key is compromised.

These edge cases are handled by the protocol by introducing the concept of spam rating and throttling of sending notification, this is done in the following way:

* The channel always starts with a spam score of neutral position \(0.5\), this rating can go towards 0 \(positive position, good actor\) or 1 \(negative position, bad actor\).
* The score is adjusted to move towards positive position \(0\) whenever a new user is added, this is weighted by the total number of users in the ecosystem as well.
* The score is adjusted to move towards negative position \(1\) whenever a user unsubscribes and indicates spam, this rating is weighted against the total number of subscribers of the channel.
* The score slowly inches towards positive position \(0\) as block number increases \(i.e. time increases\) but takes the spam score into account in relation to how quick the spam score will decrease, i.e. the higher the spam rating, the more minute adjustment is done towards the positive position.
* As the spam score start reaches or exceeds **0.8**, the number of notifications starts getting limited for a channel as a quadratic function.

{% hint style="warning" %}
The feature is expected to change heavily as it's still in development.
{% endhint %}

{% hint style="info" %}
The spam score throttle can be adjusted in the future before going to the mainnet. After mainnet, it can only be adjusted by voting mechanism of the protocol.
{% endhint %}

