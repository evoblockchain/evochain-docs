# Validators Overview

## Introduction

[EVO](../README.md) is based on [Tendermint](https://github.com/tendermint/tendermint/tree/master/docs/introduction), which relies on a set of validators that are responsible for committing new blocks in the blockchain. These validators participate in the consensus protocol by broadcasting votes which contain cryptographic signatures signed by each validator’s private key.

Validator candidates can bond their own EVOs and have EVOs ["delegated"](../delegators/delegators-guide-cli.md), or staked, to them by token holders. The EVO network will have 21 validators. The validators are determined by a ranking of those who  collected the highest number of staked EVOs— the top 21 validator candidates with the largest stakes will become EVO validators.

Validators will earn EVOs as block provisions and tokens as transaction fees through execution of the Tendermint consensus protocol and delegators should get rewards from their target validators in their own ways. Initially, transaction fees will be paid in evos but in the future, any token in the EVO ecosystem will be valid as fee tender if it is whitelisted by governance. Note that validators can set commission on the fees their delegators receive as additional incentive.

## Hardware

There currently exists no appropriate cloud solution for validator key management. This may change when cloud SGX becomes more widely available. For this reason, validators must set up a physical operation secured with restricted access. A good starting place, for example, would be co-locating in secure data centers.

Validators should expect to equip their datacenter with redundant power, connectivity, and storage backups. Having several redundant networking boxes for fiber, firewall and switching is recommended, as well as small servers with redundant hard drive and failover. 

We anticipate that network requirements will be low initially. The current testnet requires minimal resources. Bandwidth, CPU and memory requirements will rise as the network grows. Large hard drives are recommended for storing complete blockchain histories.

## Set Up a Website

Set up a dedicated validator website and signal your intention to become a validator on our [chat](https://t.me/OKevochainValidator). This is an important point since delegators will want to access essential information about the entity they are delegating their EVOs to.


## Community

Discuss the finer details of being a validator on our community chat and forum:

* [Validator Chat](https://discord.gg/VM4PRxYjtS)
