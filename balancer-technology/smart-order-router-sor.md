# Smart Order Router (SOR)

## Overview

The Smart Order Router (SOR) finds the best prices for traders. For given input and output tokens, the SOR finds the optimal trades whether that is a direct swap in one pool, or a combination of trades hopping through multiple pools.

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## Taking Gas Into Account

Since there are incremental gas costs for each exchange added to a lot, additional pools are added to the SOR route only when they provide enough price difference to compensate for the gas. Since only a subset of pools is considered, this can create arbitrage opportunities between Mistral pools.

## How It Works

The optimization mechanism finds the path through a set of Balancer Pools with the greatest output (after gas costs).

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Multiple Pools, Same Spot Price

In order to get the best price for a trader, the SOR is designed to create an arbitrage-free state between the paths it's using. In order to achieve this, **each path the SOR routes through needs to provide the same spot price after the swap has completed.**

<figure><img src="../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
