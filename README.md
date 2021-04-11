# Juno Testnets

- [Testnet 1](#testnet-1)

## Setup

You will need [Starport](https://github.com/tendermint/starport) installed. We'll be using SPN to deploy the chain and connect validators. [SPN](https://github.com/tendermint/spn) is being actively developed, please, build Starport from source and use the latest `develop` branch.

### Install and build latest Starport:

**Prerequisites:** If you want to install Starport locally, make sure to have [Golang >=1.14](https://golang.org/). The latest version of Starport also requires [Protocol Buffer compiler](https://grpc.io/docs/protoc-installation/) to be installed. [Node.js >=12.19.0](https://nodejs.org/) is used to build the welcome screen, block explorer and to run the web scaffold.

#### Build from source

Starport uses [Git LFS](https://git-lfs.github.com/). **Please make sure that it is installed before cloning Starport.**

If you have installed Git LFS after cloning Starport, checkout to your preferred branch to trigger a pull for large files or run `git lfs pull`.

```sh
git clone https://github.com/tendermint/starport --depth=1
cd starport && git checkout develop
make
```

This will build and install `starport` binary into `$GOBIN`.

Note: When building from source, it is important to have your `$GOPATH` set correctly. When in doubt, the following should do:

```sh
mkdir ~/go
export GOPATH=~/go
```

### Minimum hardware requirements

- 2GB RAM
- 25GB of disk space
- 1.4 GHz CPU

## Testnet 1

The first testnet will test using SPN to deploy the chain and connect validators.

The goal is simply to get the chain started and assess the viability of using SPN.

### Parameters

- `chainID`: `juno-testnet-1`
- `sourceURL`: https://github.com/CosmosContracts/Juno
- _Start time TBD_
- _Coordinator TBD_

### Joining as a validator

Run the following command from a server to propose yourself as a validator:

```
starport network chain join [chainID] --nightly
```

Follow the prompts to provide information about the validator. Starport will download the source code of the blockchain node, build, initialize and create and send two proposals to SPN: to add an account and to add a validator with self-delegation. By running a `join` command you act as a "validator".

By default, a coordinator does not propose themselves as a validator. To do so, run `join` command and your proposals will be automatically approved.

#### Starting your blockchain node

Run the following command to start your blockchain node:

```
starport network chain start [chainID] --nightly
```

This command will use SPN to create a correct genesis file, configure and launch your blockchain node. Once the node is started and the required number of validators are online, you will see output with incrementing block height number, which means that the blockchain has been successfully started.

### Learn more

- [Starport](https://github.com/tendermint/starport)
- [SPN](https://github.com/tendermint/spn)
- [Cosmos Network](https://cosmos.network)
- [Cosmos Community Discord](https://discord.com/invite/W8trcGV) (check out the #starport channel)