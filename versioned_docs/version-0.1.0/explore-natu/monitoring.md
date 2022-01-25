---
sidebar_position: 2
title: 'Monitoring'
keywords: [natu, blockchain, metaverse, monitoring, ecosystem, nature, conservation]
---

# Monitoring protocol

### Sumary

Having a transparent, scalable, and tamper-proof record of the conservation state of the lands in the Natu network is crucial for the long-term success of the project. In this section, we explain how the monitoring protocol works.

The Natu monitoring protocol employs a set of smart contracts in the **[NEAR blockchain](https://near.org/)**. This smart contracts manage a registry with the conservation state of lands in the network.

The **protocol divides the parks into conservation units (COUNs) of one hectare that are represented by a NFT compatible with [NEP-171 standard](https://nomicon.io/Standards/NonFungibleToken/Core.html)**. Then, we stores the data in a decentralized and inexpensive way by using the **[IPFS](https://ipfs.io/)** and referencing it in the metadata. 

Natu provides a promising approach for monitoring the lands on the network. The use of cryptography makes the registry resistant to fraud, which is crucial for distributing the rewards. Likewise, this registry is a reliable source of data for building products that run on the top of the blockchain. 

## Introduction

One of the main challenges for Natu is to monitor the state of conservation of the parks in the network. In fact, the monetary expansion depends on meeting conservation goals, see the **[economics](economics.md)**. Next, we explain how the Natu monitoring protocol works.

## Conservation Units

Natu aims to create a transparent and tamper-proof registry with the conservation state of the parks in the Natu network. We start by **dividing the lands into Conservation Units (COUNs)**. **Each COUN is a [NEP-171](https://nomicon.io/Standards/NonFungibleToken/Core.html) compliant NFT in the NEAR blockchain** that represents a square of one hectare of lands in the real world. So, the COUNs are unique, irreplaceable and identified by their geographic coordinates. 

![Parks and COUNs in Natu.](/img/coun-nft.png)

**A group of contiguous COUNs is a park**, which are the administrative entities in the real world. We define the global state of Natu network at time $t$ as the set of the states of all particular COUNs, $\theta^{t}_{c}$.

$$ 
\Theta^{t} = \{\theta^{t}_{c} \text{, such that } c \in \mathbb{C}\}
$$

Here, $\mathbb{C}$ is the set of COUNs in the network. Then, the state of COUNs is defined as the result of the processing of the data coming from monitoring devices. **The data of each COUN is stored in a decentralized and tamper-resistant manner by using the NFTs metadata and the [IPFS](https://ipfs.io/)**.

## Metadata at token level

**Every time the status of COUNs change, a smart contract updates the metadata**. The **COUNs in Natu follow the [NEP-177 standard](https://nomicon.io/Standards/NonFungibleToken/Metadata.html) to manage the metadata**. Here, the main goal is to store the important data of all the COUNs efficiently. Then, the metadata at the token level has the following structure:

```js
type TokenMetadata = {

  title: string|null, // ex. “COUN #5055”

  description: string|null, // free-form description

  media: string|null, // URL to associated media, preferably to decentralized, content-addressed storage

  media_hash: string|null, // Base64-encoded sha256 hash of content referenced by the `media` field. Required if `media` is included.

  copies: number|null, // number of copies of this set of metadata in existence when token was minted.

  issued_at: number|null, // When token was issued or minted, Unix epoch in milliseconds

  expires_at: number|null, // When token expires, Unix epoch in milliseconds

  starts_at: number|null, // When token starts being valid, Unix epoch in milliseconds

  updated_at: number|null, // When token was last updated, Unix epoch in milliseconds

  extra: string|null, // anything extra the NFT wants to store on-chain. Can be stringified JSON.

  reference: string|null, // URL to a JSON file with the conservation history of the coun.

  reference_hash: string|null // Base64-encoded sha256 hash of JSON from reference field. Required if `reference` is included.

}
```

Here, the attribute ```reference``` is an IPFS hash pointing to a JSON file that allows dApps to easily retrieve the conservation history of NFTs. The JSON file has the following structure:

```
{

    “state_hash”: “hash with the monitoring information.”

    “coun_history”: “list with all previous state (state hashes) of the coun”,

    “coun_history_hash”: “sha256(append(state_hash, prev_coun_history))”,

    “coun_data”: “an IPFS hash to the folder with the data submitted in the current period”

}
```

This **design is tamper-proof in at least two senses**. First of all, the attribute ```state_hash``` acts as a fingerprint for the monitoring process. Thus, no one can manipulate the results without altering the hash. The generation of the ```state_hash``` follows the algorithm below.

|            operation            | output hash |
| :-----------------------------: | ----------: |
|            ipfs_hash            |       hash1 |
| sha256(append(hash1,algorithm_hash)) |       hash2 |
|  sha256(append(hash2,output))   |       hash3 |
|  sha256(append(hash3,state))   | state_hash |


**Then, the smart contracts allows to mint new $NATU as rewards, according to the [economics](economics.md)**. 

Second, the ```coun_history_hash``` is a composition of all the previous states, so it acts as a proof against reordering and fraud. As a result, this protocol enables dApps to easily retrieve the data from the parks.

## Metadata at the contract level

Alike to the token level, the metadata at the contract level is 

``` js
type NFTContractMetadata = {

  spec: string, // “nft-1.0.0”

  name: string, //  “Natuverse1”. 

  symbol: string, // “COUN”.

  icon: string|null, // URL to the optimized SVG file with the logo.

  base_uri: string|null, // IPNS hash to a JSON file with the global state.

}
```

Here,  **```base_uri``` has an IPNS address pointing to a JSON file that serves as the registry of the current global state $\Theta^{t}$**. This JSON file contains the following structure:

```
{

  “global_state_hash”: “hash of the current state of all COUNs”,

  “global_state_history”: “sha256(append(global_state_hash, prev_global_state_hash))”,

  “global_state”: {

    “id coun”: “‘coun_data’, according to the token metadata”

  }

}
```

The ```global_state``` allows dApps directly fetch and verify the current state of the network. Likewise, the ```global_state_history``` is a composition of all the previous global state, making it resistant to fraud.

We presented a protocol that is scalable and decentralized due to a smart contract manages the registry and the IPFS is used for storage. Furthermore, the **protocol is tamper-proof because no one can alter the state of conservation of the COUNs or reorder them**. In conclusion, the Natu protocol provides a robust and efficient record to reward those who can show the conservation of the lands.