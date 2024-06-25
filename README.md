# RandShardsPBFT

This code implement a PBFT-based blockchain which uses the sharing mechanism and randomly assigns the nodes to the different shards.
Also, the shard to which the new request is sent is randomly chosen.

It does not implement the classification layer and does not use smart contracts.

requirements: scikit-learn==1.2.2
python version: 3.8.10

Each block contains t transactions. The t can be defined in the code (file PBFT.py lines 445 and 455?)

At present,
t = 2
n = 81
requests = 7
All the nodes are honest and rapid
