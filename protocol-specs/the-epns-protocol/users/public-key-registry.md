# Public Key Registry

## Concept

Encrypted notification generally uses algorithm based on public key or its' derivative thereof. To facilitate this, the EPNS protocol maintains a public key registry of all the users who enter the ecosystem. This is done by having mirrored function with public key registry for **creating a channel** and **subscribe** which allows the protocol to emit public key of the wallet out \(or skip if it already exists\).

{% hint style="info" %}
Since public key for any wallet is derivable if they have done even a single transaction, we consider this information as safe non-invasive to privacy. 
{% endhint %}

The public key registry for user is completely optional and the protocol has alternative methods that completely skip this process but carry the required functionality. The registry is helpful on the frontend side to quickly poll and find the key of the wallet and use it to encrypt the notifications wherever necessary.



