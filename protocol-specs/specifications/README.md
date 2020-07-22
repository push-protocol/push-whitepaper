# Specifications

EPNS is a notification protocol at its heart. We see notifications as the means to communicate information which can be of different types, carry different utilities and perform different tasks as per their use cases. To enable this, we assign each notification payload a payload type that defines certain characteristics of both the data they carry and the medium of storage. 

Besides the flexibility of notification payload, we also see the rules established between **channels** and their **subscribers** to also have an impact on their utility and use cases.

Keeping in mind with the above analogies, the following specifications are rolled out to ensure that the specifications and the payload determines the use case of the notification rather than treating them as plain standard ones.

Some of the use cases we see opening up by this approach are:

* Allowing users to receive notifications with different content type \(images, call to actions, videos, etc\) 
* Allowing future content or payload to be different and be interpreted differently
* Makes interpretation of the storage of the payload flexible as changing payload type can indicate the storage medium \(on-chain, ipfs, other storage solutions\)
* Allowing service to create channel that any user can subscribe to
* Allowing channel to approve users as subscribers and create business cases around them
* Allowing channel and users to approve each other before information is shared between them



