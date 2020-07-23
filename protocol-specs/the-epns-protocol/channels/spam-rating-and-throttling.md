# Spam rating and throttling

The protocol uses game theory and incentives to ensure that the channel stay useful to the users. However, there might come a point where a channel might become a bad actor despite the incentives and penalty imposed. This can happen in various scenarios, couple of them can be:

* Popular channel is bought by someone else with the purpose to promote advertisements
* Channel private key is compromised

These edge cases are handled by the protocol by introducing the concept of spam rating and throttling of sending notification, this is done in the following way:

* The channel always starts with a spam rating of neutral position \(0.5\), this rating can go towards 0 \(positive position, good actor\) or 1 \(negative position, bad actor\).
* The ratings are adjusted to inch towards positive position \(0\) whenever a new user is added, this is weighted by the total number of users in the ecosystem as well.
* The ratings are adjust to inch towards negative position \(1\) whenever a user unsubscribes and indicates spam, this rating is weighted against the total number of subscribers of the channel.
* The ratings slowing inches towards positive position \(0\) as block number increases \(ie: time increases\) but takes the spam rating into account for decreasing the spam score, ie: the higher the spam ratings is, the more minute adjustment is done towards positive position.
* As the spam rating starts reaching or exceeding **0.8**, the number of notifications starts getting limited for a channel as a quadratic function.

{% hint style="warning" %}
The feature is expected to change heavily as its still in development.
{% endhint %}

