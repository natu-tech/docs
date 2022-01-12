---
sidebar_position: 3
title: 'Economics'
keywords: [natu, blockchain, metaverse, token, tokenomics, economics, ecosystem, nature, conservation]
---

# Economics

### Sumary

Natu aims to create a conservation network through a system of incentives based in a fungible cryptocurrency called \$NATU.

From the economic side, the monetary expansion of \$NATU depends on the monitoring of the parks of the network. Likewise, the demand comes from the usage of the products that run on the NatuChain.

Natu is an innovative approach to create an open and green economy that reward those who conserve nature.

## Introduction

One of the fundamental parts of Natu is its mechanism to reward those who conserve nature. 

The Natu economics is based on the monitoring results to determine the distribution of rewards. Here, \$NATU is the native currency for paying rewards in the NatuChain. 

From the economics side, the **monetary expansion is a result of the conservation of ecosystems**. Likewise, the **demand for \$NATU comes from the usage of products build on top of the NatuChain**.

![Natu economics overview.](/img/economics-intro.png) 

To fulfill Natu’s promise of value, which is to create the largest conservation network in the world, we created a **[roadmap](/roadmap/overview)** that is made up of stages. As the figure shows, \$NATU will be the native currency of the NatuChain and its entire ecosystem.

## \$NATU

Once the Biome stage is reached, the NatuChain and its native currency \$NATU will be launched to the market. From the economic side, **the supply of \$NATU is limited to 1.618 bn**. Here, **each \$NATU is generated because of the monitoring results**, according to the **[monetary policy](#monetary-policy-tokenomics)**. 

On the other side, **\$NATU is conceived as the means of payment within the Natu ecosystem**, so the demand comes from the use of the products that run on the NatuChain.

### Use cases for \$NATU

Use cases are the main demand for \$NATU. If \$NATU adoption increases, the demand will grow and viceversa. In other words, **\$NATU gain value if more people use it**, and more people will use \$NATU if we provide a good development tool that increases the utility of the coin.

There are two primary use cases. First, the **\$NATU balance will serve for voting power calculation in the [NatuDAO](/explore-natu/community)**. Here, the DAO allows the community to fund projects aligned with the vision of Natu through on-chain voting processes. Second, **$NATU will serve as currency for companies that use the NatuChain to develop their business model**. 

### Monetary policy (tokenomics)

Natu’s monetary policy aim to address the following issues

- The need to **promote the geographic growth of the Natu conservation network**.

- The need to **offer rewards for participats in the network**.

- The need to ensure the **economic sustainability of Natu** in the long run.

We propose a monetary policy in which the **new minted coins depend not only on the conservation of each PLOT but also on its neighbors**, see the **[monitoring protocol](/explore-natu/monitoring)** for more information. In the first place, let be $c_{k}(t)$ the conservation status of the PLOT $k$ in the time $t$,

$$
 c_{k}(t) = \left\{ \begin{array}{lc}

1 & \text{if $PLOT_{k}$ was conserved,} \\

0 & \text{if $PLOT_{k}$ is impossible to conserve,}\\

 -\frac{1}{3} & \text{if $PLOT_{k}$ is not conserved.}

\end{array}
 \right.
$$

Then, $n_k(t)$ represents the reward in \$NATU corresponding to the conservation of PLOT $k$ in the period $t$,

$$
n_{k}(t,M) =   c_{k} \cdot \left(  \sum_{j \in \Lambda}{c_{j}} + 1 \right) \cdot r_{k}(t,M) \ ,
$$

where $\Lambda$ is the set of neighbours PLOTs, $t$ is the current time from the genesis block, and $M$ is the total number of PLOTs. By its part, the reward factor $r_{k}(t,M)$ is

$$
r_{k}(t,M) = \left( g(t) \cdot h(M) + 0.01 \right) \cdot r_{0,k} \  .
$$

Here, $g(t)$ is a function that decreases linearly with time

$$
 g(t) = 1.1^{- \left(\frac{t}{3} - 1\right)} \ \ .
$$

It is important to note that incorporating more PLOTs implies a higher monetary expansion. To address this, **we integrate the** $h(M)$ **function to algorithmically prevent the inflation**. This function reduces the reward factor as a function of the number of PLOTs in the network,

$$
h(M) = 1.1^{- \left( \frac{M}{10^{6}}-1 \right)} \ \ .
$$

![The reward factor decreases over time and when there are more lands in the network.](/img/reward-factor.png)

---

**NOTE**

The risk factor $r_{0, k}$ will be implemented through a Natu Improvement Proposal (NIP) in the Tundra stage. Until then, we will use $r_{0, k} = 1$ for all PLOTS.

---

## Token allocation

The allocation of new minted \$NATUs aims to **compensate for the decrease in rewards** for those who keep their land in the network for a long period. Likewise, we seek to **ensure a predictable source of income** that allows the development of Natu in both the adoption and the technology.

The token allocation starts with the NatuChain mainnet launching. Here, **the income of each participant is made up of the new allocation of minted coins plus the distribution of transaction fees**. 

**The initial supply of \$NATU is zero and all new $NATUs will be distributed among the landowners, the validators nodes, and the Natu Foundation**. The distribution varies with time according to the following figure

![Token allocation.](/img/token-allocation.png)

The **token distribution aims to motivates early adopters to move quickly to benefit from high initial rewards**. At the same time, the incentive structure works because the **stakeholders can benefit from additional fees if the number of transactions increases over time**. These extra fees will compensate for the smaller rewards when the max supply of \$NATU is close to being reached. As a result, the Natu reward mechanism provide a predictable source of income for all stakeholders in the long run. 

Then, it is possible to calculate the distribution of new minted tokens for each participant. In fact, the portion that belongs to the landowners at time $t$ from the genesis block in the NatuChain is

$$
A_{L} [\%] = \left\{ \begin{array}{llc}

1.875 \cdot (t - 16) + 70 & \text{if } & t \leq 16\\

70 & \text{if} & t > 16

\end{array}
\right.
$$

For its part, the portion of new minted tokens belonging to the Natu Foundation is 

$$
A_{N} [\%] = \left\{ \begin{array}{llc}

- 0.9375 \cdot (t - 16) + 15 & \text{if } & t \leq 16\\

15 & \text{if} & t > 16

\end{array}
\right.
$$

Likewise, the validators nodes receives a part of the new emission according to:

$$
A_{D} [\%] = \left\{ \begin{array}{llc}

- 0.9375 \cdot (t - 16) + 15 & \text{if } & t \leq 16 \\

15 & \text{if} & t > 16

\end{array}
\right.
$$

---
**NOTE**

The periodicity of the distribution of the new tokens and the amount of the transaction fees will be discussed in the Tundra era, see the **[roadmap](/roadmap/overview)**.

---

## Examples of reward calculation

In the following, we report on the simulation of three scenarios. The purpose is to show the reward calculation on a clear path. In these examples we assume that we are in the first year since the launch of NatuChain ( $t=1$ ), there are 1,000 PLOTs in the network ( $M = 1,000$ ) and the risk factor is 1 ( $r_{0,k} = 1$ ). We also consider that the distribution is 41.9% to landowners, 29.05% to Natu Foundation and 29.05% to the validators. 

Then, we analyze the **minimum viable park. It is composed of 3 contiguous PLOTs and is the smallest admitted park on the network**. Here, the total reward for each period of two month is $0.394$ \$NATU, and the average reward per PLOT is equal to $0.131$ \$NATU.

![Minimum viable park in Natu network.](/img/mvp.png)

The distribution of these new minted tokens is 0.165 \$NATU to the landowner, 0.114 \$NATU to the Natu Foundation and 0.114 $NATU to the validators.

On the other hand, we now study a 9-PLOTs park that could represent a big natural park in the network. Then, we assess the case in which one central PLOT is not being conserved and the impact on its surroundings.

![Parks and plots in Natu.](/img/8vs9-plots.png)

We observe that **the average reward per PLOT increases by $83\%$ when conserving continuous parks**. As a result, there is a powerful reason to grow parks through collaborative work. Indeed, all neighbors benefit from protecting an extra PLOT.

## What happens when the maximum supply is reached?

It is important to ensure the continuity of the conservation network once the maximum supply of tokens is reached. To address this issue, **we propose to fund a treasure by charging a small transaction fee on the NatuChain**. 

The amount of the transaction fees and its distribution will be discussed in later stages, see the **[roadmap](/roadmap/overview)**.

## Conclusion

The design of the tokenomics creates an extra incentive for early adopters as they can benefit from higher initial rewards. Also, we ensure the sustainability of the conservation network by incorporating a small transaction fee in the NatuChain.

At the same time, the **token allocation for \$NATU provides predictable income for all stakeholders**. This allows for the continuous development of Natu. Finally, the limited supply of 1.618 billion can turn $NATU into a promising store of value for the future.

