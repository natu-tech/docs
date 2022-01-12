---
sidebar_position: 2
title: 'Monitoring'
keywords: [natu, blockchain, metaverse, monitoring, ecosystem, nature, conservation]
---

# Monitoring protocol

---
**NOTE**

The complete monitoring protocol for the NatuChain will be presented after the Tundra era. There will be something like a “Proof of Conservation” for the NatuChain. See the **[roadmap](/roadmap/overview)**.

---


### Sumary

Having a transparent, scalable, and tamper-proof record of the conservation state of the lands in the Natu network is crucial for the long-term success of the project. In this section, we describe how the Natu monitoring protocol works. 

The **Natu monitoring protocol employs a set of smart contracts** in the NatuChain. This smart contracts manage a registry with the conservation state of lands in the network. 

The protocol **divides the parks into PLOTS of one hectare that is represented by a NFT in the NatuChain**. Then, we **stores the data in a decentralized and inexpensive way by using [IPFS](https://ipfs.io/) and referencing it in the metadata**. Also, Natu uses cryptography to make the protocol resistant to fraud.

The Natu protocol is a promising approach for monitoring the lands on the network. In fact, this system provides a verified record to distribute rewards. Also, it creates a reliable source of data for developing products that run on the top of the NatuChain.

## Introduction

One of the main challenges for Natu is to implement a protocol for monitoring the state of conservation of the parks in the network. Having a good design allows a smart contract to expand the monetary supply in a transparent way, according to the **[reward policy](economics.md)**. Furthermore, it provides a validated data source for creating products that run on top of Natu. Next, we explain how the Natu monitoring system works.

## Conservation State

The **Natu monitoring system aims to create a transparent and tamper-proof registry with the conservation state of the parks** in the Natu network. We start by dividing the lands into PLOTs, which are the minimum units of conservation in Natu. Each PLOT is a NFT in the NatuChain that represents a square of one hectare of land in the real world. So, the **PLOTs are unique, irreplaceable and identified by their geographic coordinates**. 

![Parks and plots in Natu.](/img/plot-nft.png)

**A group of contiguous PLOTs is a PARK**, which are the administrative entities in the real world. We define the global state of Natu network at time $t$ as the set of the states of all the PLOTs $\theta^{t}_{p}$.

$$ 
\Theta^{t} = \{\theta^{t}_{p} \text{, such that } p \in \mathbb{P}\}
$$

Here, $\mathbb{P}$ is the set of plots in the network. Then, the state of PLOTs is defined as the result of the processing of the data coming from monitoring devices. **The data of each PLOT is stored in a decentralized and tamper-resistant manner by using the NFTs metadata and the IPFS**.

## Metadata at token level

**Every time the state of PLOTs change, a smart contract updates the metadata**. The PLOTs in Natu will follow the standards in Natu (NIPs) to manage the metadata. Here, the main goal is to store the relevant data of all the PLOTs efficiently. As a result, the metadata at the token level has the following structure: 

```js
type TokenMetadata = {

  title: string|null, // ex. “Plot #5055”

  description: string|null, // free-form description

  media: string|null, // URL to associated media, preferably to decentralized, content-addressed storage

  media_hash: string|null, // Base64-encoded sha256 hash of content referenced by the `media` field. Required if `media` is included.

  copies: number|null, // number of copies of this set of metadata in existence when token was minted.

  issued_at: number|null, // When token was issued or minted, Unix epoch in milliseconds

  expires_at: number|null, // When token expires, Unix epoch in milliseconds

  starts_at: number|null, // When token starts being valid, Unix epoch in milliseconds

  updated_at: number|null, // When token was last updated, Unix epoch in milliseconds

  extra: string|null, // anything extra the NFT wants to store on-chain. Can be stringified JSON.

  reference: string|null, // URL to a JSON file with plot conservation history.

  reference_hash: string|null // Base64-encoded sha256 hash of JSON from reference field. Required if `reference` is included.

}
```

Here, the ```reference``` attribute is an IPFS hash pointing to a JSON file that allows dApps to easily retrieve the conservation history of PLOTs. The JSON file has the following structure:

```
{

    “state_hash”: “hash with the monitoring information.”

    “plot_history”: “list with all previous state (state hashes) of the plot”,

    “plot_history_hash”: “sha256(append(state_hash, prev_plot_history))”,

    “plot_data”: “ipfs hash to the folder with the data submitted in the current period”

}
```

This **design is tamper-proof in at least two senses**. First of all, the variable ```state_hash``` acts as a fingerprint for the monitoring process. Thus, no one can manipulate the results without altering the hash. The ```state_hash``` is generated following the algorithm below.

|            operation            | output hash |
| :-----------------------------: | ----------: |
|            ipfs_hash            |       hash1 |
| sha256(append(hash1,algorithm_hash)) |       hash2 |
|  sha256(append(hash2,output))   |       hash3 |
|  sha256(append(hash3,state))   | state_hash |


**Then, the smart contract issues the rewards, according to the [monetary policy](economics.md)**. 

In the second place, the ```plot_history_hash``` is a composition of the previous states, so it acts as a proof against reordering and tamper. As a result, this protocol enables dApps to easily retrieve validated data from PLOTs.

## Metadata at the contract level

Alike to the token level, the metadata at the contract level is 

``` js
type NFTContractMetadata = {

  spec: string, // “nft-1.0.0”

  name: string, //  “Natuverse1”. 

  symbol: string, // “PLOTS”.

  icon: string|null, // URL to the optimized SVG file with the logo.

  base_uri: string|null, // IPNS hash to a JSON file with the global state, see X.

}
```

Here,  **```base_uri``` has an IPNS address pointing to a JSON file that serves as the registry of the current global state $\Theta^{t}$**. This JSON file contains the following structure:

```
{

  “global_state_hash”: “hash of the current state of all PLOTs”,

  “global_state_history”: “sha256(append(global_state_hash, prev_global_state_hash))”,

  “global_state”: {

    “id parcel”: “‘plot_data’, according to token metadata”

  }

}
```

The ```global_state``` allows dApps directly retrieve and verify the current state of the network. At the same time, the ```global_state_history```  is a composition of the previous global state, making it resistant to reordering and tamper.

We presented a protocol that is scalable and decentralized due to a smart contract manages the registry and the IPFS is used for storage. Furthermore, the **protocol is tamper-proof because no one can alter the state of conservation of the plots or reorder them**. In conclusion, the Natu protocol provides a robust and efficient record to reward those who can show the conservation of the lands.