# 2.2 Activation of a service

The protocol requires a service to activate themselves by creating a **channel** , The activation requires them staking 50 DAI \(at the time of writing\) or higher on the protocol, which is then deposited in a interest generating protocol \(AAVE at the time of writing\), which in turn is shared by all the subscribers of the service as a reward. 

The protocol attaches weights and indexes to all the services and subscribers in order to distribute the interest earned in a weighted manner among the subscribers, the weight always prefers the earliest block number or the earliest subscriber \(ie: user who subscribe of block 1 will earn more than the subscriber of block 10\).

