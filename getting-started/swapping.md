# Swapping

## How do I make my first swap?

First time here?&#x20;

In short, you'll need:

* KLAY to pay for gas fees
* Desired tokens to trade
* A Klaytn address you can use with one of the following compatible wallets
  * MetaMask
  * Kaikas (TM)

## What is Price Impact?

Price Impact is how much the price of an asset changes during a swap. Since prices in AMMs depend directly on token balances, and a swap creates a change in balances, the spot price in the pool changes.

## What is Slippage?

Slippage is the change in token prices between when you create a transaction and when it actually executes. To make sure you get within the price range you expect, trades have Slippage Tolerances. You can change this tolerance by in the Slippage settings.



## What is the Smart Order Router?

The Smart Order Router (SOR) is a system that intelligently sources liquidity from multiple pools so as to automatically figure out the best available price from the range of available pools. You can set it to use V1 or V2 only; by default it finds the best path using both.



## Can I trade if I have no tokens?

Yes\*\*\*\*\*, Flash Swaps allow arbitrageurs to find and swap imbalanced pools and claim the difference as profit. Since only final net amounts are transferred, arbitrage trades are also significantly easier. An arbitrageur who has no tokens but detects a price asymmetry between pools could trade DAI for MKR in pool 1, MKR for BAL in pool 2 then BAL for DAI in pool 3 and end up making a profit in DAI.

**\***You'll still need ETH to pay gas fees

## What happens if my transaction fails?

Unfortunately, if your transaction fails you will lose your gas fees. Miners collect these gas fees when attempting to execute your trade; they are not collected by Mistral.
