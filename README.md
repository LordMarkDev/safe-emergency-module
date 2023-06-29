# Safe Emergency Module

## Problem to solve

The Safe’s multi-signature feature works by requiring a minimum number of signatures from the Safe’s signers to approve any transaction, if the minimum number of signers can’t be achieved, the whole safe with all the funds will remain locked forever. This can be a remote possibility but it can happen in case of disaster, like plane crashes, fires, earthquakes or loss of wallets, and in our opinion it is not acceptable, especially for Safes with large balances, like DAO or Company treasuries.

## Project overview

We propose the “Safe Emergency Module”, a Safe App that can take “Emergency actions” after a chosen “Inactivity time”, avoiding the risk that the Safe’s funds will remain locked forever.
The configurable “Emergency actions” that we propose are:

- Add/Replace the chosen addresses as Safe signers
- Set the minimum number of signatures to the desired amount

The configured “Emergency actions” can be triggered by anyone after that the “Inactivity time” has elapsed.
To monitor the Safe “Inactivity time” we will implement a “Keep alive” system, based on a button that will trigger a transaction updating the “Last activity time”. This button has to be pressed before the expiration of the “Inactivity time”. The system will automatically send reminders (as emails) to the configured signer’s email addresses when the expiration is approaching.

## About us

### MARCO NEGRONI (@LordMarkDev)
Safe Guardian, Senior .NET and Web3 full stack developer, Tech researcher; I have about 10 years of professional experience.
[https://www.linkedin.com/in/lordmarkdev](https://www.linkedin.com/in/lordmarkdev)

### STEFANO BELLOTTI (@stefanob77)
Computer engineer, senior software developer with 20+ years of experience on all major programming languages and platforms. Crypto enthusiast and trader.
[https://www.linkedin.com/in/stefano-bellotti-868681198](https://www.linkedin.com/in/stefano-bellotti-868681198)

## Specification

We will develop the Emergency Module smart contract (as Safe Module), the web3 integration (as Safe App) and the backend notifications system (for off-chain scheduled tasks).
