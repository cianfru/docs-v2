# The Mistral Vault

## Overview <a href="#overview" id="overview"></a>

The Vault acts as a smart contract responsible for holding and managing all the tokens present in each pool. In addition, it serves as the primary portal for conducting various operations such as swaps, joins, and exits.

## Separating Token Accounting and Pool Logic <a href="#separating-token-accounting-and-pool-logic" id="separating-token-accounting-and-pool-logic"></a>

The Vault architecture is designed to separate token accounting and management from pool logic, resulting in simplified pool contracts that no longer require active management of its assets. Pools only need to calculate amounts for swaps, joins, and exits. The Vault architecture also accommodates various pool designs, as it is agnostic to pool math and can support any system that satisfies specific requirements. As a result, users can come up with a novel idea for a trading system and create a custom pool that is directly integrated into Balancer's existing liquidity, eliminating the need to build their own decentralized exchange.

<figure><img src="https://1718773110-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Friurf5v1s63ePRkLXbsZ%2Fuploads%2Fgit-blob-0676f94276c01842db6b9d7584d5d9892865a221%2Fvault.png?alt=media" alt=""><figcaption></figcaption></figure>

## Gas Efficient Batch Swaps <a href="#gas-efficient-batch-swaps" id="gas-efficient-batch-swaps"></a>

Compared to other decentralized exchanges that pair token accounting with pool logic, multi-hop trading (A->B->C) can be expensive due to the need to transfer ERC20 tokens at each hop. However, our unique advantage lies in the architecture, where all tokens are stored in the same contract, The Vault. This allows for more efficient swaps as tokens no longer need to be transferred at each step of a multi-hop trade. Instead, The Vault maintains internal records of which pool holds which tokens, and only transfers tokens at the input and output stages. This streamlined process significantly reduces the number of token transfers required, resulting in substantial gas savings.

<figure><img src="https://1718773110-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2Friurf5v1s63ePRkLXbsZ%2Fuploads%2Fgit-blob-2232b6faf647159c30364344d50965de428ba565%2Fgascomparisonbatchswap.png?alt=media" alt=""><figcaption></figcaption></figure>

#### Internal Balances <a href="#internal-balances" id="internal-balances"></a>

Expanding on the idea of reducing token transfers, Mistral has taken it a step further by enabling swaps that require no token transfers at all. By extending the functionality of the Vault, which already maintains token balances for pools, Mistral now allows for balances to be maintained for any Ethereum address. Users can hold Internal Balances in the Vault and execute trades to and from these balances, without the need for actual token transfers.

## Security <a href="#security" id="security"></a>

An important aspect to consider is that the Vault is specifically designed to maintain the independence of pool balances. This is especially crucial in a permissionless system where any user can create their own tokens and pools. By ensuring this independence, Mistral protects against malicious or poorly designed tokens or custom pools that could potentially drain funds from other pools. It's worth noting that although the Vault may consolidate liquidity of a specific token from multiple pools, the depth of combined liquidity does not impact the price of tokens in individual pools.

## Flash Loans <a href="#flash-loans" id="flash-loans"></a>

While the combined liquidity in the Mistral Vault does not affect the price impact on a per-pool basis, it does provide the protocol with an advantage in terms of Flash Loans. Flash Loans are loans that do not require any collateral, but must be repaid with interest in the same transaction as they were borrowed. The transaction must be completed within a single block, ensuring that borrowers cannot abscond with the tokens.

Moreover, Mistral Protocol enables anyone to execute a Flash Swap if they detect a price discrepancy in two pools. With Flash Swaps, arbitrageurs do not need to hold any of the input tokens required to make a trade. Instead, they identify the price difference, instruct the Vault to execute the swap, and earn a profit as a result.
