### FundMe Smart Contract Documentation

## Description

FundMe is an Ethereum smart contract that allows users to fund the contract with Ether (ETH) based on a minimum USD value. It utilizes Chainlink price feeds for obtaining the latest ETH/USD conversion rate and ensuring that the funded ETH amount meets a specified minimum in USD. The contract is designed to collect funds from multiple users and enable the owner to withdraw the collected funds.

## Contract Details

### State Variables

1. s_addressToAmountFunded: A mapping that associates an Ethereum address with the amount of ETH they have funded.

2. s_funders: An array containing Ethereum addresses of users who have funded the contract.

3. i_owner: The address of the contract owner, set during contract deployment.

4. MINIMUM_USD: A constant representing the minimum amount in USD that must be spent when funding the contract.

5. s_priceFeed: An instance of the Chainlink AggregatorV3Interface contract used to fetch the ETH/USD conversion rate.

### Functions

1. fund(): Allows users to fund the contract by sending ETH. Requires the sent ETH to meet or exceed the specified minimum USD value based on the current ETH/USD conversion rate.

2. getVersion(): Retrieves the version of the Chainlink price feed.

3. cheaperWithdraw(): Allows the contract owner to withdraw all the collected funds, resetting fund balances and funders' list.

4. withdraw(): Similar to cheaperWithdraw(), but performs the withdrawal through a different method, using the call function.

5. getAddressToAmountFunded(address fundingAddress): Retrieves the amount of ETH funded by a specific address.

6. getFunder(uint256 index): Retrieves the Ethereum address of a funder at a specific index in the s_funders array.

7. getOwner(): Retrieves the address of the contract owner.

### Modifiers

1. onlyOwner(): A modifier that restricts certain functions to be callable only by the contract owner.

## License

This contract is licensed under the MIT License.

Contract Deployment

## Contract Deployment

This guide will walk you through the process of deploying the FundMe smart contract to the Sepolia network, along with automated contract verification on Etherscan. The deployment process is automated using a Makefile and environment variables.

### Step 1: Set Up Environment Variables

1. Create a copy of the .example.env file and name it .env.
2. Fill in the environment variables in the .env file:
    - SEPOLIA_RPC: The Sepolia RPC URL.
    - PRIVATE_KEY: Your Ethereum wallet private key.
    - ETHERSCAN_API_KEY: Your Etherscan API key.

### Step 2: Write and Deploy the Contract
1. Make sure you have the FundMe contract and deployment script ready.
2. Use the following command to build the contract (if needed):

```shell
$ make build
```

3. Deploy the FundMe contract to the Sepolia network and verify it on Etherscan using the following command:

```shell
$ make deploy-sepolia
```
