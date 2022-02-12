---
sidebar_position: 4
title: 'Natunomics'
keywords: [natu, blockchain, token, tokenomics, economics, natunomics, ecosystem, nature, conservation]
---

# Natunomics

## Sumary

Natu aims to create the largest conservation network in the world through a system of incentives called **Natunomics**. Likewise, the Natunomics is based on a **protect to earn (P2E)** principle that distributes rewards to the park owners. These rewards are paid in \$NATU, a **[NEP-141](https://nomicon.io/Standards/FungibleToken/Core.html)** compliant token in the **[NEAR blockchain](https://near.org/)**.

From the economic side, **the supply of \$NATU is limited to 1.618 bn** and the **monetary expansion of \$NATU is 1% per month**. Likewise, **all the transaction fees are burned** to take the 12% of the circulating supply per year out of circulation. At the same time, **\$NATU serve as the native currency in the Natu ecosystem**, so the demand comes from its adoption. 

## Introduction

We all benefit from living in a world with more protected ecosystems. In fact, we can **[mitigate the effects of climate change if we protect ecosystems](https://doi.org/10.1038/s41558-020-00976-6)**. However, we see the nature protection as an expense, not as an investment. As a consequence, the **[world has lost a third of its forests since the last ice age](https://ourworldindata.org/world-lost-one-third-forests)** and **[most coral reefs could be gone in 20 years](https://news.agu.org/press-release/warming-acidic-oceans-may-nearly-eliminate-coral-reef-habitats-by-2100/)** if we continue on this path.

One of the main causes is that the **landowners bear an opportunity cost by keeping their land idle**. In fact, they could always dedicate themselves to ranching, growing rice or selling land to companies that do not care about the environment.

**Natu aims to build the largest conservation network** in the world through a system of incentives called Natunomics. The Natunomics is based on a **protect to earn (P2E)** principle that distributes rewards to the landowners who turn their land into parks. These rewards are paid in \$NATU, a **[NEP-141](https://nomicon.io/Standards/FungibleToken/Core.html)** compliant token in the **[NEAR blockchain](https://near.org/)**.

![Natu economics overview.](/img/economics-intro.png) 

## \$NATU token

**\$NATU is a [NEP-141](https://nomicon.io/Standards/FungibleToken/Core.html) fungible token** in the **[NEAR blockchain](https://near.org/)** that acts as the currency for the Natu’s ecosystem. 

The token $NATU aim to address three main issues. First, the need to **promote the geographic growth of the Natu conservation network**. Second, the need to achieve **the long-term commitment of park owners**. Third, the need to ensure the **economic sustainability of Natu in the long run**.

### Use cases

Use cases are the main demand for \$NATU. If \$NATU adoption increases, the demand will grow and vice versa. In other words, **\$NATU gain value if more people use it**, and more people will use \$NATU if there are use cases that increases the utility of the token.

---
**NOTE**

The implementation of the use cases follows the **[roadmap](/roadmap/overview)**.

---

### Tokenomics

We propose a **Protect to earn model (P2E)** where the **initial supply of \$NATU is zero** and the only way to get rewards is to meet conservation goals. Likewise, tokenomics allows the issuance of new \$NATU tokens if the circulating supply $s$ is less than the **maximum supply $S$, which is set at 1.618bn**. 

Controlling the monetary expansion while maintaining rewards for the park owners is crucial in the medium and long term, so we created two control mechanisms. First, we mint and **distribute 1% of the maximum supply each month**. Likewise, **we incorporated a dynamic burn rate** that charges a small transaction fee based on the daily traded volume $v(t)$, relative to the circulating supply. The goal is to **burn 12% of the circulating supply per year**. 

With this in mind, we can see the evolution of the token supply over time.

![Circulating supply over time.](/img/supply.png)

### Protect to earn

In our **protect to earn (P2E)** model, the rewards depend not only on the conservation of each conservation unit (COUN), but also on the status of its neighbors. 

Let be $c_{k}(t)$ the conservation status of the COUN $k$ in the time $t$ as

$$
 c_{k}(t) = \left\{ \begin{array}{lc}

1 & \text{if $COUN_{k}$ was conserved,} \\

0 & \text{if $COUN_{k}$ is impossible to conserve,}\\

 -\frac{1}{3} & \text{if $COUN_{k}$ is not conserved.}

\end{array}
 \right.
$$

Then, each COUN has a conservation score $\phi_{k}(t)$ that determines its participation in the monthly distribution of rewards

$$
 \phi_{k}(t) = c_{k}(t) \cdot \left( \sum_{j \in \Omega_{N}}{c_{j}(t)} + 1 \right) \cdot \tau_{k}(t) , 
$$

Here, $\Omega_{N}$ is the set of neighbours COUNs, and

$$
\tau_{k}(t) = 1 + tanh\left(\frac{t-t_{0}}{5}\right)  
$$

is a factor that amplifies the rewards for parks that have been in the network for a long time, where $t_{0}$ is the time (in years) when the park joined the network. Likewise, let the total conservation score $\Phi(t)$ be the sum of all the individual scores

$$
 \Phi(t) = \sum_{j \in \Omega(t)} \phi_{j}(t) , 
$$

with $\Omega(t)$ being the set of all COUNs in the network. Then, $n_{k}(t)$ represents the reward in \$NATU corresponding to the conservation of the COUN $k$

$$
 n_{k}(t) = \frac{\phi_{k}(t)}{ \Phi(t) } \cdot r(t) \cdot S ,
$$

where $r(t) = 0.01$ is the reward factor corresponding to the 1% of the maximum supply of \$NATU.


### Token allocation

The allocation of new minted \$NATUs aims to **ensure a predictable source of income** that allows the development of Natu in both the adoption and the technology. 

The new minted tokens are distributed among the park owners (60%), the Natu Foundation (30%), and the natuDAO (10%). 

## Examples

In the following, we report on the simulation of three scenarios. The purpose is to show the reward calculation on a clear path. In these examples we assume that we are in the first year since launch ( $t=1$, $r_{k}(t) = 1$ ), there are 10,000 COUNs in the network ( $M = 10,000$ ) and the total score is 90,000 ($\Mu = 90,000$). We also consider that the reward distribution is 60% to landowners, 30% to Natu Foundation and 10% to the natuDAO.

First, we analyze the **minimum viable park**. It is composed of 3 contiguous COUNs and is the smallest admitted park on the network. After calculations, the total score for all COUNs is 0.394, resulting in a reward of 70.83 $NATU, with the average reward per COUN equal to 42.50 \$NATU. Likewise, the distribution of these new minted tokens is 36.12 \$NATU to the park owner, 21.25 \$NATU to the Natu Foundation and 7.83 $NATU to the natuDAO.

![Minimum viable park in Natu network.](/img/mvp.png)

On the other hand, we now study a 9-COUNs park that could represent a big natural park in the network. Then, we assess the case in which one central COUN is not being conserved and the impact on its surroundings.

![Parks and couns in Natu.](/img/8vs9-couns.png)

We observe that **the average reward per COUN increases by 105% when conserving continuous parks**. As a result, there is a powerful reason to grow parks through collaborative work. Indeed, all neighbors benefit from protecting an extra COUN.

## Conclusion

We get several benefits from this design. First of all, **the early adopters benefit from high rewards**. Second, **the burning rate is low for users** and **higher adoption implies lower transaction fees**. Third, the **burn rate ensures the sustainability of the project in the long run**, because the incomes are predictable and the rewards never ends for park owners who meet the conservation goals.
