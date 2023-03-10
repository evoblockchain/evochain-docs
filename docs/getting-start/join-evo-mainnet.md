# Join the Public Mainnet 

See the [mainnet repo](https://github.com/evoblockchain/mainnet) for
information on the latest mainnet, including the correct version
of EVO to use and details about the genesis file.

**You need to [install evo](./install-evo.md) before you go further**

## Supported Platforms

We support running a full node on `Mac OS X`, `Windows` and `Linux`.

## Minimum System Requirements

The hardware must meet certain requirements to run `evochaind`.

 * Desktop or laptop hardware running recent versions of Mac OS X, Windows, or Linux.
 * 500 GB of free disk space, accessible at a minimum read/write speed of 100 MB/s.
 * 4 cores of CPU and 8 gigabytes of memory (RAM).
 * A broadband Internet connection with upload/download speeds of at least 1 megabyte per second

## Setting Up a New Node

These instructions are for setting up a brand new full node from scratch.

First, initialize the node and create the necessary config files:

```bash
evochaind init <your_custom_moniker>
```

> _NOTE_:
Monikers can contain only ASCII characters. Using Unicode characters will render your node unreachable.


Or you can also edit this `moniker` later, in the `~/.evochaind/config/config.toml` file:

```toml
# A custom human readable name for this node
moniker = "<your_custom_moniker>"
```

You can edit the `~/.evochaind/config/evochaind.toml` file in order to enable the anti spam mechanism and reject incoming transactions with less than the minimum gas prices("0.000000001evo" is recommended):

```
# This is a TOML config file.
# For more information, see https://github.com/toml-lang/toml

##### main base config options #####

# The minimum gas prices a validator is willing to accept for processing a
# transaction. A transaction's fees must meet the minimum of any denomination
# specified in this config (Our recommended quantity is  10^-9 evo).

minimum-gas-prices = "0.000000001evo"
```

Your full node has been initialized! 

## Genesis & Seeds

### Copy the Genesis File

Fetch the mainnet's `genesis.json` file into `evochaind`'s config directory.

Note we use the `latest` directory in the [mainnet repo](https://github.com/evoblockchain/mainnet) which contains details for the mainnet like the latest version and the genesis file. 

To verify the correctness of the configuration run:

```bash
evochaind validate-genesis
```

### Add Seed Nodes

Your node needs to know how to find peers. You'll need to add healthy seed nodes to `$HOME/.evochaind/config/config.toml`. The [mainnet repo's](https://github.com/evoblockchain/mainnet) README.md contains some seed nodes.

You can add those seeds nodes to the `seeds` filed in the `~/.evochaind/config/config.toml` file:

```toml
# Comma separated list of seed nodes to connect to
seeds = "e926c8154a2af4390de02303f0977802f15eafe2@3.16.103.80:26656,7fa5b1d1f1e48659fa750b6aec702418a0e75f13@175.41.191.69:26656,c8f32b793871b56a11d94336d9ce6472f893524b@35.74.8.189:26656"
```

For more information on seeds and peers, you can [read this](https://docs.tendermint.com/master/spec/p2p/peer.md).

## Starting a New Node

Start the full node with this command:

```bash
evochaind start --chain-id evochain-66
```

Check that everything is running smoothly:

```bash
evochaincli status
```

See the [mainnet repo](https://github.com/evoblockchain/mainnet) for information on mainnet, including the correct version of the EVO to use and details about the genesis file.


## JSON-RPC Endpoint
[RPC URL](../developers/blockchainDetail/aminorpc.md#mainnet-chain-id-evochain-66)


## Upgrading Your Node

These instructions are for full nodes that have ran on previous versions of and would like to upgrade to the latest mainnet.

### Reset Data

First, remove the outdated files and reset the data.

```bash
rm $HOME/.evochaind/config/addrbook.json $HOME/.evochaind/config/genesis.json
evochaind unsafe-reset-all
```

Your node is now in a pristine state while keeping the original `priv_validator.json` and `config.toml`. If you had any sentry nodes or full nodes setup before,
your node will still try to connect to them, but may fail if they haven't also
been upgraded.

> _NOTE_:
Make sure that every node has a unique `priv_validator.json`. Do not copy the `priv_validator.json` from an old node to multiple new nodes. Running two nodes with the same `priv_validator.json` will cause you to double sign.


### Software Upgrade

Now it is time to upgrade the software:

```bash
git clone https://github.com/evoblockchain/evochain.git
cd evochain
git fetch --all && git checkout vx.y.z
make install
```

> _NOTE_: If you have issues at this step, please check that you have the latest stable version of GO installed.

Note we use `master` here since it contains the latest stable release.
See the [mainnet repo](https://github.com/evoblockchain/mainnet) for details on which version is needed for which mainnet, and the [EVO release page](https://github.com/evoblockchain/evochain/releases) for details on each release.

Your full node has been cleanly upgraded!

### Upgrade to Validator Node

You now have an active full node. What's the next step? You can upgrade your full node to become a EVO Validator. The top 100 validators have the ability to propose new blocks to the EVO. Continue onto [the Validator Setup](../validators/validators-guide-cli.md).
