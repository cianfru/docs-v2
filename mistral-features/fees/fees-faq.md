# Fees FAQ

## What type of fees are there?

* Trading fees: A small percentage of the trade paid by traders to pool LPs, set by the pool creator or dynamically optimized.\
  \
  For instance, if a pool had a 1% fee, and governance introduced a 1% protocol fee - the total swap fee to the trader would remain at 1%, but now 0.99% would accrue to the pool's LPs, and 0.01% would accrue to the protocol fee collector contract.\\
* Flash Loan fees: A small percentage of assets that are used for flash loans from Mistral vault. This is the protocol fee - it accrues to the protocol, for allocation by governance.

## What are the fees for a trade?

Mistral Pools are extremely customizable, and each pool can have a different fee. It is up to the pool creator to decide how high the fees should be, ranging from 0.0001% to 10%. When using the Smart Order Router, the fees will always be taken into account when finding the best price.

## Why do pools have Dynamic Fees?

Today, it’s nearly impossible to choose a correct swap fee at pool creation time. Inherently, the optimal trading fee for a pair continuously changes throughout both tokens’ lifecycles and the overall market cycle.

For example, a static fee can have diminishing returns after circumstances change, like liquidity moving to another pool. Another example is that during times of wild volatility, liquidity providers risk sustaining greater impermanent losses.
