# Traceable dNFT Ledger

## Introduction
Traceable dNFT Ledger (TdL) is a blockchain-based dynamic NFT ledger that assures real-time synchronization with the on-chain data and high-throughput NFT updates. This project is designed by Matrix Labs to meet the needs for a backend for high throughput dNFT applications. 
## Key Features
### **Bi-directional real-time synchronization with multiple blockchains**
TdL synchronizes all on-chain events from multiple blockchains in real-time and updates the state of the corresponding NFT in the ledger. In the other direction, Traceable dNFT Ledger can also publish the up-to-date NFT data through Oracle APIs to the blockchain. 
### **Traceability of NFT change history**
TdL is backed by a blockchain and public IPFS. All changes made to the NFT’s state will be recorded by the underlying blockchain. Therefore, users can trace back and verify the change history of all NFTs via the Log Verifier. 
### **Programmability and customizability**
Developers can write customized handlers to process both on-chain and off-chain events to tailor to the needs of various dNFT projects.
### **Dynamic NFT compatible**
TdL is fully compatible with dynamic NFT standards and supports multiple blockchains and marketplaces. 
### **High throughput**
TdL can handle very high TPS for complex dNFT scenarios such as real-time games.
## Architecture
![Traceable dNFT Ledger - Page 1](https://user-images.githubusercontent.com/55181785/181468746-48a868e9-a21c-44e1-a10f-f12e007957f5.png)
### **Event Handler**
TdL’s Event Handler is fronted by the NFT metadata ledger that receives events emitted from an upstream blockchain (e.g., Ethereum, Aptos, Flow, etc.) in a subscription fashion or events from specific authorized servers/users. These events will trigger certain metadata mutation logic and mutate the metadata stored in the Metadata Ledger. 
### **NFT Metadata Ledger**
Metadata ledger is backed by a blockchain (i.e., not necessarily a blockchain network, can also be a centralized blockchain for better performance), and all the metadata mutation history its data integrity is guaranteed by cryptography. 
### **Metadata Resolver**
Metadata Resolver is responsible for providing the resolved metadata to consumers such as wallets or NFT marketplaces. Different transform and resolving logics can be added to meet the various consumers’ data formats. 
### **Metadata Explorer**
TdL’s metadata explorer is a web app for users to browse and verify the metadata change history stored in the blockchain ledger for transparency and justice purposes. Users can query the metadata of a specific token and see how it is mutated from the initial states. It will also support range queries for the metadata histories of a collection of tokens. 
## Use Cases
### **Event-driven backend for dNFT projects**
TdL can handle both on-chain and off-chain events from either blockchain or authorized users. Developers can write their own customized handler scripts to process and dynamically mutate NFT states and publish the metadata to various marketplaces. A blockchain-based computation engine processes all the mutation, and all the NFT images and 3D models are persisted in the IPFS network.  
### **Trace NFT change history; verification and replay**
Metadata Explorer allows the user to trace the all-time NFT change history easily. Since TdL is backed by a blockchain, all users can easily query against the blockchain to browse the raw transactions, verify the event handling process, and replay the events. 
### **Scaling the dNFT backend for high throughput dApp**
TdL is backed by scalable blockchains such as dedicated private or high-speed public blockchains. This design allows dApp to scale up without worrying about the TPS limitation on most mainstream blockchains. When using a dedicated private blockchain as a backend, Traceable dNFT Ledger can achieve up to 3000 TPS, and it is sufficient for most high throughput dApp such as blockchain games. 
## NFMS and Traceable dNFT Ledger
### **Mutate NFTs’ state and appearance from on-chain events**
TdL can synchronize on-chain **newBlock** events to accumulate EXP points for players who hold NFTs. When an NFT character is upgraded after gaining a certain amount of EXP, the Event Handler script can also update its appearance (new image or animation), which can be viewed in all marketplaces in real time. 
![01](https://user-images.githubusercontent.com/55181785/181468690-a31046ba-290d-403a-80d7-9dcc86e070f2.png)

### **Mutate the NFT state with authentication**
Traceable dNFT Ledger can also receive authed off-chain events issued by the NFT’s owner. Once the authentication is verified, the off-chain event will be handled, and the corresponding updates will be added to Traceable dNFT Ledger and recorded in the blockchain backend. For example, the NFT’s owner can change the weapon after authenticated via his/her crypto wallet and Traceable dNFT Ledger will instantly update the NFT’s appearance.
![02](https://user-images.githubusercontent.com/55181785/181468702-495d7524-b7f2-4d7e-bbcf-190155f3fb17.png)

### **Browse mission logs and verify the NFT mutation history**
All the missions that happened off-chain will be pushed to the Event Handler and will be persisted in the NFT Metadata Ledger. Players can use Log Verifier Web UI to browse and verify the mission logs and NFT mutation history for every NFT. 
![03](https://user-images.githubusercontent.com/55181785/181468715-2bdd81e1-226c-44e2-bfff-0ab030dead07.png)

