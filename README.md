## Quickstart

1. Clone and install dependencies

Then:
```
yarn
```

or
```
npm i
```

2. You can now do stuff!

```
yarn hardhat test
```

# Usage

If you run `yarn hardhat --help` you'll get an output of all the tasks you can run. 

## Deploying Contracts

```
yarn hardhat deploy
```

This will deploy your contracts to a local network.

## Run a Local Network

One of the best ways to test and interact with smart contracts is with a local network. To run a local network with all your contracts in it, run the following:

```
yarn hardhat node
```

You'll get a local blockchain, private keys, contracts deployed (from the `deploy` folder scripts), and an endpoint to potentially add to an EVM wallet. 

To deploy contracts:

```
yarn hardhat deploy --network goerli
```

To run staging testnet tests
```
yarn hardhat test --network goerli
```

# Test
Tests are located in the [test](./test/) directory, and are split between unit tests and staging/testnet tests. Unit tests should only be run on local environments, and staging tests should only run on live environments.

To run unit tests:

```
yarn hardhat test
```
or

```
yarn hardhat test --network goerli
```

## Performance optimizations

Since all tests are written in a way to be independent from each other, you can save time by running them in parallel.

To run tests in parallel:
```
yarn test --parallel
```
or
```
yarn hardhat test --parallel
```
or
```
yarn hardhat test
```

You can make Hardhat run faster by preventing ts-node from recompiling and type-checking your project on every run by setting the `TS_NODE_TRANSPILE_ONLY` env variable to 1:
```
TS_NODE_TRANSPILE_ONLY=1 yarn test
```

## Verify on Etherscan

You'll need an `ETHERSCAN_API_KEY` environment variable. You can get one from the [Etherscan API site.](https://etherscan.io/apis). If you have it set, your deploy script will try to verify them by default, but if you want to verify any manually, you can run: . If you have it set, your deploy script will try to verify them by default, but if you want to verify any manually, you can run: 

```
yarn hardhat verify --network <NETWORK> <CONTRACT_ADDRESS> <CONSTRUCTOR_PARAMETERS>
```
example:

```
yarn hardhat verify --network goerli 0x9279791897f112a41FfDa267ff7DbBC46b96c296 "0x9326BFA02ADD2366b30bacB125260Af641031331"
```

# View Contracts Size

```
yarn run hardhat size-contracts
```

# Linting

This will [lint](https://stackoverflow.com/questions/8503559/what-is-linting) your smart contracts.  

```
yarn lint:fix
```

# Code Formating

This will format both your typescript and solidity to look nicer. 

```
yarn format
```

# Estimaging Gas

To estimate gas, just set a `REPORT_GAS` environment variable to true, and then run:

```
yarn hardhat test
```

If you'd like to see the gas prices in USD or other currency, add a `COINMARKETCAP_API_KEY` from [Coinmarketcap](https://coinmarketcap.com/api/documentation/v1/).

# Code coverage

To see a measure in percent of the degree to which the smart contract source code is executed when a particular test suite is run, type
```
yarn coverage
```