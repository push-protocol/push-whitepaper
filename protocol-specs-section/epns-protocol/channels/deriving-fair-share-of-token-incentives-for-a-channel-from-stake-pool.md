# Deriving fair share of token incentives for a channel from stake pool

## Concept

The stake pool is a pool that contains all the staking fees from all the channels. There are two important concepts to keep in mind to derive the fair share of token incentives for an individual channel.

* The staking fee starts earning token incentives as soon as a channel is activated, this means that the fair share of a channel would need to account for the time since the channel is activated to ensure fair play. This is achieved by recording the **block number** at which a channel is activated.
* The staking fee is dynamic and can differ from one channel to another, i.e. channel decides the amount based on their game theory and incentive plan they put in place. To account for this, the **weight** of the channel and **aggregated weight of all channels** are recorded at the time a new channel creation.

## Problem Statement

We need to derive the formula which gives us the ratio of the token incentives the channel has generated so that it can be distributed among the subscribers fairly proportionate to their joining of the channel and the number of subscribers joined earlier. 

While this can be solved by recursion of all channels, getting their share in the pool, deriving their weight and the start block number. This will be inefficient as more channels continue to get activated on the protocol. 

### Solution

Instead of recursion, we are going to approach the formula in a linear way. We know that each time a channel is added, the previous number of channels, their block number, etc can be treated like a constant as their values will not change moving forward. 

For example, if **channel** **x** got added at **block y**, then the channels count before **block y** would never change, nor will the differential which we have before **channel** **x** was added. We utilize this to form our own ratio calculation that is not based on recursion but instead is based on the aggregation that happens whenever a channel is added or removed. The different weights of the channel are also mapped to an aggregated weight variable which helps us in determining the total sum needed to derive the fair share of token incentives for the channel.

Putting it together, the formula by which we can derive a channels' fair share of token incentives from the stake pool for current block can be written as:

### Formula to calculate fair share token incentives ratio

$$
ratio = (d * a) / (z + n * x  *w)
$$

### Formula to calculate historical constant \(z\) 

Occurs whenever a channel is added, deactivated or the stake fees changes

$$
z = z + (n * x  * w)
$$

| Parameter | Explanation |
| :--- | :--- |
| d | Differential of current block number and the block number on which the channel was last modified in relation to stake fee. |
| a | The actual weight of the channel, measured by dividing the stake fee of the channel with the minimum stake fee. |
| z | The historical constant of the **channels**, calculated whenever a modification in number of channels occurs or whenever  the stakes fee of the channel is changed. |
| n | The previous count of the number of channels present in the protocol. |
| x | Differential between the latest block number and the last modified block number. Last modified block number is whenever a channel was added, deactivated or fees of any channel was changed. |
| w | The averaged out weight of all the channels, the average is normalized / averaged out whenever a new channel is added, deactivated or fess of any channel is changed. |

