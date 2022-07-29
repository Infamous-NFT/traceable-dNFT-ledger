# TdL Aptos Implementation Proposal

## Introduction

This page introduces the proposal of implementing TdL using Aptos as the blockchain-based metadata ledger backend.

## Architecture
![Aptos (2)](https://user-images.githubusercontent.com/55181785/181701970-f53fbffc-40c0-4de6-a8df-ffc7f7cb2215.png)

### Event Handler Contract
Event Handler is a module/smart contract deployed to Aptos that only received authed users and data sources. Event Handler will contain the customized logic to handle the events and mutate the metadata by invoking APIs of Metadata Contract. The permission control is also implemented inside the module itself for better transparency. 

### Metadata Contract
The metadata ledger in TdL is also in the form of Aptos modules/smart contracts. It will expose APIs only to Event Handler to update the metadata using the `friend` keyword in Move. We will also use Move's `Table` for scalable metadata ledger implementation. Metadata Contract will also expose public read-only APIs for query, verification, and visibility purposes. 
Currently, the metadata Contract is designed for multi-tenant purposes and will allow different NFT collections to store their metadata in the same module. We will add more details of this part later.

### NFT Contract
The actual NFT module contains the NFT ownership and other necessary information. The only difference between this module and the official tutorial one (https://aptos.dev/tutorials/your-first-nft/) is the metadata is derived from the Metadata Contract instead of from the module itself. 

### Metadata Explorer
A Web app that will give users the ability to browse the mutation history of metadata that is stored in the Metadata Contract.

## Milestone
- Permission control for Event Handler (WIP)
- Event Handler template
- Metadata Contract deployed in Aptos Devnet
- Metadata Explorer deployed in Aptos Devnet
- Aptos Devnet launch

## Open Questions & Risks

- N/A 
