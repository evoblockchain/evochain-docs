# Install EVO

This guide will explain how to install the `evochaind` and `evochaincli` entrypoints
onto your system. With these installed on a server, you can participate in the
testnet as either a [Full Node](./join-evo-mainnet.md) or a
[Validator](../validators/validators-guide-cli.md).

## Install Go

Install `go` by following the [official docs](https://golang.org/doc/install).
Remember to set your `$PATH` environment variable, for example:

```bash
mkdir -p $HOME/go/bin
echo "export PATH=$PATH:$(go env GOPATH)/bin" >> ~/.bash_profile
echo "export GOPATH=$HOME/go" >> ~/.bash_profile
echo "export GOBIN=$GOPATH/bin" >> ~/.bash_profile
echo "export PATH=$PATH:$GOBIN" >> ~/.bash_profile
source ~/.bash_profile
```
Under Windows, you may set environment variables(`HOME` or `GO111MODULE`) through the "Environment Variables" 
button on the "Advanced" tab of the "System" control panel. Some versions of Windows 
provide this control panel through the "Advanced System Settings" option inside the 
"System" control panel.

> _NOTE_: **Go 1.17+** is required for the EVO.


## Install the binaries

Next, let's install the latest version of EVO. Make sure you `git checkout` the [latest released version](https://github.com/evoblockchain/evochain/releases).

```bash
git clone -b <latest-release-tag> https://github.com/evoblockchain/evochain
export GO111MODULE=on
cd evochain 
# mainnet, use make mainnet
make mainnet
# testnet, use make testnet
make testnet
```
Under Windows, you can execute the below commands on PowerShell to set the environment variable `GO111MODULE`.
```shell script
# Enable the go modules feature
$env:GO111MODULE="on"
```

If this command fails due to the following error message, you might have already set `LDFLAGS` prior to running this step.

```
# github.com/evoblockchain/evochain/cmd/evochaind
flag provided but not defined: -L
usage: link [options] main.o
...
make: *** [install] Error 2
```

Unset this environment variable and try again.

```
LDFLAGS="" make install
```

> _NOTE_: If you still have issues at this step, please check that you have the latest stable version of GO installed.

That will install the `evochaind` and `evochaincli` binaries. Verify that everything is OK:

```bash
$ evochaind version --long
$ evochaincli version --long
```

`evochaincli` for instance should output something similar to:

```shell
name: evochain
server_name: evochaind
client_name: evochaincli
version: v1.6.5
commit: 4f496351ab3bdc4ce014706711f31589021dd0de
build_tags: netgo
go: go version go1.19.2 darwin/amd64
```

### Build Tags

Build tags indicate special features that have been enabled in the binary.

| Build Tag | Description                                     |
| --------- | ----------------------------------------------- |
| netgo     | Name resolution will use pure Go code           |
| ledger    | Ledger devices are supported (hardware wallets) |

### Install binary distribution via snap (Linux only)

**Do not use snap at this time to install the binaries for production until we have a reproducible binary system.**

## Developer Workflow

To test any changes made in the Cosmos-SDK or Tendermint, a `replace` clause needs to be added to `go.mod` providing the correct import path.

- Make appropriate changes
- Add `replace github.com/cosmos/cosmos-sdk => /path/to/clone/cosmos-sdk` to `go.mod`
- Run `make install` or `make build`
- Test changes

## Next

Now you can [join the mainnet](./join-evo-mainnet.md), [the public testnet](./join-evo-testnet.md) or [create you own testnet](./deploy-you-own-evo-testnet.md)
