---
sidebar_position: 3
title: 'Economics'
keywords: [natu, blockchain, metaverse, token, tokenomics, economics, ecosystem, nature, conservation]
---

# Economics

### Sumary

Natu aims to create a conservation network through a system of incentives based on \$NATU, a **[NEP-141](https://nomicon.io/Standards/FungibleToken/Core.html)** compliant token in the **[NEAR blockchain](https://near.org/)**.

From the economic side, the monetary expansion of \$NATU depends on the conservation state of the parks in the network. **The supply of \$NATU is limited to 1.618 bn tokens**. Likewise, the demand comes from the usage of its ecosystem. Indeed, **\$NATU serve as the currency for buying products, lands, and services in the metaverse**.

## Introduction

One of the fundamental parts of Natu is its mechanism to reward those who conserve nature. 

The Natu economics is based on the monitoring results that determine the distribution of rewards. From the economic side, the monetary expansion of \$NATU depends on the conservation state of the parks in the network. Likewise, the demand comes from the usage of its ecosystem. Indeed, **\$NATU serve as the currency for buying products, lands, and services in the metaverse**.

![Natu economics overview.](/img/economics-intro.png) 

To fulfill Natu’s promise of value, which is to create the largest conservation network in the world, we created a **[roadmap](/roadmap/overview)** that is made up of eras.

## \$NATU

**\$NATU is a fair-launch [NEP-141](https://nomicon.io/Standards/FungibleToken/Core.html) fungible token** that acts as the currency for the Natu’s ecosystem. Therefore, **the initial supply of \$NATU is zero** and the monetary expansion depends on the conservation state of the parks in the network. Here, **the maximum supply of \$NATU is limited to 1.618 bn**.

### Use cases for \$NATU

Use cases are the main demand for \$NATU. If \$NATU adoption increases, the demand will grow and vice versa. In other words, **\$NATU gain value if more people use it**, and more people will use \$NATU if we provide a good development tool that increases the utility of the token.

#### Buying lands in natutowns

Every time 1,000,000 new lands (COUNs) are added to the Natu Conservation Network, then a new synthetic village of 1,618 hectares is created in the **[natuverse](/explore-natu/natuverse)**.

Each locality is divided into parcels of 0.5 hectares called LANDS. **Each LAND is a [NEP-171 standard](https://nomicon.io/Standards/NonFungibleToken/Core.html) on the [NEAR blockchain](https://near.org/)**. Here, **\$NATU serves as a means of payment to buy and rent LANDs in the natutowns**.

For more information about natutowns and its LANDs, see the **[natuverse](/explore-natu/natuverse)** section.


#### Rent spaces in natutowns

Each natutown is designed as an open and safe space in which the community can interact. These new forms of interaction will create new products, services and even jobs. **\$NATU is intended to be the currency to pay for goods and services in the natuverse**.

Some examples are the rental of spaces for advertising or stores. Users will also be able to pay architects to design and build real estate on their lands.

#### Buying NFTs and products

The Natuverse is a platform where developers can create new businesses that ultimately generate value for the community. \$NATU will be the currency to buy these products and services. In fact, **users will be able to use their \$NATU to buy artwork, game skins and avatars, concert tickets, and more**.

#### Participate in decentralized voting processes

**The balance of \$NATU is used to calculate the voting power of each individual in the [NatuDAO](/explore-natu/natudao)**. The NatuDAO allows the users to fund and promote their favorite projects through decentralized voting processes.

### Monetary policy (tokenomics)

Natu’s monetary policy aim to address the following issues

- The need to **promote the geographic growth of the Natu conservation network**.

- The need to **offer rewards for participants in the network**.

- The need to ensure the **economic sustainability of Natu** in the long run.

We propose a monetary policy in which the **new minted coins depend not only on the conservation of each COUN but also on its neighbors**, see the **[monitoring protocol](/explore-natu/monitoring)** for more information. In the first place, let be $c_{k}(t)$ the conservation status of the COUN $k$ in the time $t$,

$$
 c_{k}(t) = \left\{ \begin{array}{lc}

1 & \text{if $COUN_{k}$ was conserved,} \\

0 & \text{if $COUN_{k}$ is impossible to conserve,}\\

 -\frac{1}{3} & \text{if $COUN_{k}$ is not conserved.}

\end{array}
 \right.
$$

Then, $n_k(t)$ represents the reward in \$NATU corresponding to the conservation of the COUN $k$ in the time $t$ (since launch),

$$
n_{k}(t,m) =   c_{k} \cdot \left(  \sum_{j \in \Lambda}{c_{j}} + 1 \right) \cdot r_{k}(t,m) \ .
$$

Here $\Lambda$ is the set of neighbours COUNs, $s$ is the circulating supply of \$NATU, and $m$ is the number of COUNs in the network. Likewise, the reward factor $r(s)$ is computed as

$$
r(s,M) = 1 - \frac{s}{S} \,
$$

where, $S$ is the **maximum supply of 1.618 bn \$NATU** ($s \leq S$).

---
**NOTE**

Tokenomics allows the issuance of new \$NATU tokens if the circulating supply is less than the maximum supply.

---

It is important to point out that integrating more COUNs into the network implies a greater monetary expansion and consequently more inflation. To address this issue, **we incorporate a dynamic burn rate** that depends on the daily traded volume $v$ in the form of a little transaction fee

$$
b(v)[\%] = 1 - 1.618^{-\frac{v}{S}} 
$$

We get several benefits from this design. First of all, **the burning rate is demonstrably capped at 0.38\%**, which represents a very small fee for the users. Second, the burn rate depends on the daily volume traded, so **higher adoption means more tokens burned** and more future rewards for the park owners. Finally, the inclusion of this **burn rate ensures the sustainability of the project in the long run**, because the rewards never end if there is demand for the token. 


### Token allocation

The allocation of new minted \$NATUs aims to **compensate for the decrease in rewards** for those who keep their land in the network for a long period. Likewise, we seek to **ensure a predictable source of income** that allows the development of Natu in both the adoption and the technology.

**The income of each participant is made up of the new allocation of minted tokens plus the distribution of little transaction fees**. The token distribution varies with time according to the following figure

![Token allocation.](/img/token-allocation.png)

The distribution of new tokens aims to encourage **early adopters to move quickly to benefit from high initial rewards**. Likewise, Natu seek to the long-term commitment of the park owners, whereby **they will receive a share of the transaction fees**. So then, the park owners can benefit from additional fees if adoption increases over time. 

These extra fees will compensate for the smaller rewards when the max supply of \$NATU is close to being reached. As a result, the Natu reward mechanism provide a predictable source of income for all stakeholders in the long run.

It is possible to calculate the distribution of new minted tokens for each participant. In fact, the portion that belongs to the parkowners at time $t$ from launch 

$$
A_{L}(t) [\%] = \left\{ \begin{array}{llc}

50 + t & \text{if } & t \leq 10\\

60 & \text{if} & t > 10

\end{array}
\right.
$$

For its part, the portion of new minted tokens belonging to the Natu Foundation is 

$$
A_{N}(t) [\%] = \left\{ \begin{array}{llc}

- 1.5 \cdot t  + 50 & \text{if } & t \leq 10\\

35 & \text{if} & t > 10

\end{array}
\right.
$$

Likewise, the natuDAO receives a part of the new emission according to:

$$
A_{D}(t) [\%] = \left\{ \begin{array}{llc}

0.5 \cdot t & \text{if } & t \leq 10 \\

5 & \text{if} & t > 10

\end{array}
\right.
$$

---
**NOTE**

The periodicity of the distribution of the new tokens is monthly, but the amount of the transaction fees will be discussed in the Tundra era, see the **[roadmap](/roadmap/overview)**.

---

## Examples of reward calculation

In the following, we report on the simulation of three scenarios. The purpose is to show the reward calculation on a clear path. In these examples we assume that we are in the first year since launch ( $t=1$ ), there are only 1,000 COUNs in the network ( $M = 1,000$ ) and the risk factor is 1 ( $r_{0,k} = 1$ ). We also consider that the distribution is 51% to landowners, 48.5% to Natu Foundation and 0.5% to the natuDAO.

Then, we analyze the **minimum viable park. It is composed of 3 contiguous COUNs and is the smallest admitted park on the network**. Here, the total reward for each period of one month is $0.394$ \$NATU, and the average reward per COUN is equal to $0.131$ \$NATU.

![Minimum viable park in Natu network.](/img/mvp.png)

The distribution of these new minted tokens is 0.2009 \$NATU to the landowner, 0.1911 \$NATU to the Natu Foundation and 0.0019 $NATU to the natuDAO.

On the other hand, we now study a 9-COUNs park that could represent a big natural park in the network. Then, we assess the case in which one central COUN is not being conserved and the impact on its surroundings.

![Parks and couns in Natu.](/img/8vs9-couns.png)

We observe that **the average reward per COUN increases by $83\%$ when conserving continuous parks**. As a result, there is a powerful reason to grow parks through collaborative work. Indeed, all neighbors benefit from protecting an extra COUN.

## What happens when the maximum supply is reached?

It is important to ensure the continuity of the conservation network once the maximum supply of tokens is reached. To address this issue, **we propose to fund a treasure by charging a small transaction fee**. 

The amount of the transaction fees and its distribution will be discussed in later eras, see the **[roadmap](/roadmap/overview)**.

## Conclusion

The design of the tokenomics creates an extra incentive for early adopters as they can benefit from higher initial rewards. Also, we ensure the sustainability of the conservation network by incorporating a small transaction fees.

At the same time, the **token allocation for \$NATU provides predictable income for all stakeholders**. This allows for the continuous development of Natu.
