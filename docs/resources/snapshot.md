# EVO Snapshot

Quick instructions on how to install the EVO snapshots.

According to the snapshot size, it is divided into S0, S1, S2 and S3:

 - S0. size of s0 is the smallest, including only the last block and the state of that height.
 - S1. --pruning everything: larger than S0 size
 - S2. --pruning default: larger than S1 size
 - S3. --pruning nothing: maximum size

Meaning of [pruning parameter](https://forum.evo.club/d/58-pruning)


## testnet
Download URL: [https://static.evoblock.com/cdn/oec/snapshot/index.md](https://static.evoblock.com/cdn/oec/snapshot/index.md)

For the differences between snapshots, please refer to：[this](https://forum.evo.club/d/169-oec)


## mainnet
Download URL: [https://static.evoblock.com/cdn/oec/snapshot/index.md](https://static.evoblock.com/cdn/oec/snapshot/index.md)

For the differences between snapshots, please refer to：[this](https://forum.evo.club/d/169-oec)


## Unpack the snapshot file for cosmos
```shell
mv ~/.evochaind/data ~/.evochaind/data-bak
# rm -rf ~/.evochaind/data
cd ~/.evochaind 
tar -zxvf evochain-$version-$date-$height_xxx.tar.gz
```
