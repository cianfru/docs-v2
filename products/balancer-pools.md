---
cover: ../.gitbook/assets/download.jpeg
coverY: -91.2927191679049
---

# Mistral Pools

Pools are at the core of the Mistral Protocol; What makes Mistral's Pools unique from those of other protocols is their limitless flexibility. While other exchanges have pools with constrained parameters, Mistral can accommodate pools of any composition and underlying math. Mistral allows for anyone to develop their own pool type, opening the door for customized pricing functions in trading pools.

### Weighted Pools

Weighted liquidity pools are liquidity pools with an unorthodox token distribution. Supporting up to 8 assets, users can choose any **token** they wish to create a pool with and distribute it independently.

Each token is assigned a weight defining what fraction of the pool is made up by each asset. Weighted pool equation is a generalization of the x\*y=k by accounting for uneven weights and more assets:

$$
V = \prod_t B_t^{W_t}
$$

where V is constant, B is an asset's balance, and W is an asset's weight in the pool.

_Weighted_ often means token weights are divided liberally and not necessarily 50-50 like a traditional pool. Popular examples on Mistral include the 80/20 $MSTRL-$KLAY pool which has a ratio of 80% $MSTRL tokens & 20% $KLAY.

This means that when a user deposits liquidity in the 80/20 $MSTRL-$KLAY pool, the exposure to $MSTRL's performance would be higher than $KLAY's.

Weighted pools allow for strategizing with your portfolio while providing liquidity at the same time. Users can have more exposure to stablecoins than volatile assets during bearish markets & vice versa during bullish markets.

The technology behind weighted pools also gives the side-effect of curbing impermanent loss if weighted accordingly.

### Stable Pools

Pools consisting of stablecoins, meant for stableswaps. The added benefit of Mistral's stable pools is that they offer low fees at 0.01% per swap. This makes swapping on Mistral a lot more attractive for users with larger quantities, thus attracting more volume.

Certain assets are expected to consistently trade at near parity (e.g. different varieties of stablecoins or synthetics) This efficient design is the StableSwap AMM  by Curve. Users can use these pools for larger trades while encountering major price impact.&#x20;

### Boosted Pools

Boosted pools are pools where the liquidity pairs are comprised of yield-bearing tokens. When a user swaps through the pool, the tokens pulled from the farm & distributed to the swapper. When the swap is over, the pool deposits the tokens from the trade & earns yield again.

### Metastable Pools

MetaStable Pools are an extension of Stable Pools that contain tokens with known exchange rates. MetaStable Pools use [Stable Math](broken-reference) in conjunction with this known exchange rate. They are great for tokens with highly correlated, but not pegged, prices.

## Comparison

| Pool           |     Math | Max # Tokens | Uses Oracle | Can _Be_ Oracle | Time-dependent pricing |
| -------------- | -------: | -----------: | ----------: | --------------: | ---------------------: |
| **Weighted**   | Weighted |            8 |          No |             Yes |                     No |
| **Stable**     |   Stable |            5 |          No |              No |                     No |
| **MetaStable** |   Stable |            2 |         Yes |             Yes |                     No |
| **Managed**    | Weighted |           50 |          No |              No |                    Yes |
