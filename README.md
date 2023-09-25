# Safe Emergency Module

## Problem to solve

The Safe’s multi-signature feature works by requiring a minimum number of signatures from the Safe’s signers to approve any transaction, if the minimum number of signers can’t be achieved, the whole safe with all the funds will remain locked forever. This can be a remote possibility but it can happen in case of disaster, like plane crashes, fires, earthquakes or loss of wallets, and in our opinion it is not acceptable, especially for Safes with large balances, like DAO or Company treasuries.

## Project overview

We propose the “Safe Emergency Module/Hook (hybrid solution)”, a ready to scale Safe App that can take “Emergency actions” after a chosen “Inactivity time”, avoiding the risk that the Safe’s funds will remain locked forever.
The configurable “Emergency actions” that we propose are:

- Add/Replace the chosen addresses as Safe signers
- Set the minimum number of signatures to the desired amount

The configured “Emergency actions” can be triggered by anyone after that the “Inactivity time” has elapsed.
To monitor the Safe “Inactivity time” we will implement a “Keep alive” system, that can be based:

- On a button that will trigger a transaction updating the “Last activity time”. This button has to be pressed before the expiration of the “Inactivity time” (compatible with all versions of Safe and keeps the same gas costs for the Safe transactions).

- On the smart contract, added also as Safe Hook, updating the "Last activity time" after each executed transaction (compatible only with Safes 1.3.0+ and adds additional gas costs to each Safe transaction).

We just check the "Last activity time", because on-chain we cannot get info about the last made transaction and using off-chain data is not safe for this kind of mechanism and brings to centralization.

The system will automatically send reminders (as emails) to the configured signer’s email addresses when the expiration is approaching.

## About us

### MARCO NEGRONI (@LordMarkDev)
Safe Guardian, Senior .NET and Web3 full stack developer, Tech researcher; Over 10 years of professional experience.

[https://github.com/LordMarkDev](https://github.com/LordMarkDev)
[https://www.linkedin.com/in/lordmarkdev](https://www.linkedin.com/in/lordmarkdev)

### STEFANO BELLOTTI (@stefanob77)
Computer engineer, senior software developer with 20+ years of experience on all major programming languages and platforms. Crypto enthusiast and trader.

[https://www.linkedin.com/in/stefano-bellotti-868681198](https://www.linkedin.com/in/stefano-bellotti-868681198)

## Specification

We will develop the Emergency Module smart contract (as Safe Module/Hook), the web3 integration (as Safe App) and the backend notifications system (for off-chain scheduled tasks).

We planned to develop the following features: 
- User-friendly UI for configuration and setup (including module/hook smart contract deployment)
- Visualization and editing of the “Emergency Action”:
  - List of new address to be added as safe owners
  - New threshold amount
- View and edit the timeout for the “Emergency Action”
- View the Safe “Last Activity Timestamp” and the remaining time until the “Emergency Action” can be triggered
- Visualization and editing of the list of email addresses for notification of imminent timeout
- Visualization and editing of the list of email addresses for notification of expired timeout
- “Keep Alive” button to update the “Last Activity Timestamp” (in the case the Safe Hook is not initialized but the module is installed)
- Automatic update of the “Last Activity Timestamp” with Safe Hook (optional)
- Automatic email notifications of imminent or expired timeout

## Tech stack

- Vercel - [https://vercel.com](https://vercel.com)
- NextJS - [https://nextjs.org](https://nextjs.org)
- React - [https://react.dev](https://react.dev)
- Tailwind - [https://tailwindcss.com](https://tailwindcss.com)
- Solidity - [https://soliditylang.org](https://soliditylang.org)
- Hardhat - [https://hardhat.org](https://hardhat.org)
- TrailOfBits Ethereum Security Toolbox (Slither) - [https://github.com/trailofbits/eth-security-toolbox](https://github.com/trailofbits/eth-security-toolbox)
- Ethers - [https://docs.ethers.org](https://docs.ethers.org)
- SafeAppsSDK - [https://docs.safe.global/safe-core-aa-sdk/safe-apps](https://docs.safe.global/safe-core-aa-sdk/safe-apps)
- SafeContracts - [https://github.com/safe-global/safe-contracts](https://github.com/safe-global/safe-contracts)
- MongoDB Atlas - [https://www.mongodb.com/atlas/database](https://www.mongodb.com/atlas/database)
- AWS Lambda - [https://aws.amazon.com/it/lambda](https://aws.amazon.com/it/lambda) or EvenNode - [https://www.evennode.com](https://www.evennode.com) or similar
