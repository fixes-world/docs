---
description: The standard Fungible Tokens in Fixes World
---

# 💹 Fixes Coins

## Concept

**Coins**, provided a one-stop solution for launching, distributing, and trading Flow Standard Fungible Tokens[\[Example\]](https://github.com/onflow/flow-ft).

It is the best place to launch your meme coin on Flow Blockchain. It not only provides a trading experience similar to [pump.fun](https://pump.fun/), but also provides optional allocation modes for token issuers to use.

**Fair, Safe, Powerful.** That's the core feature that the Fixes Coins always adheres to.

## Features

### Unruggable

All Flow Fungible Tokens launched by the Fixes Coins are deployed on newly created keyless Flow addresses based on the [HybridCustody](https://github.com/onflow/hybrid-custody/) protocol. Therefore, only the Fixes platform contract can manage several methods of these Coins such as initializing the allocation module by using HybridCustody. Since these coins are deployed in keyless Flow addresses controlled only by the Fixes platform contract, once the coin issuers choose to "Renounce" and have the Fixes platform contract removing the coins from its sub-account, they will become truly ownerless "Renounced" Coins.

Note: Due to Flow's Crescendo upgrade, Fixes will temporarily hold on the "Fully Renounce" feature. The network upgrade requires each FT contract upgraded to Cadence 1.0, so the platform temporarily needs to retain the right to update contracts. It will be open after the Crescendo Upgrade.

### Build-in Trading

Once the Tradable module is activated, the coin will immediately mint all the tokens allocated in this module and deposit them in the Tradable Pool with the built-in Bonding Curve.

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Tradable Pool</p></figcaption></figure>

_**The Tradable Pool has two trading stages**_

1. In-Pool Phase: Because of the Bonding Curve, users can buy and sell coins at any time using the Tradable Pool contract. The price of the Coin is calculated based on the formula of the Bonding Curve.
2. IncrementFi Phase: When the market cap of the Tradable Pool reaches $32k, all liquidity and corresponding proportions of coins will be migrated to IncrementFi. The functions on UI will also automatically adjust to call IncrementFi's liquidity pool's token swap.

_**LP Locking(Burning)**_

* All LP tokens migrated from Tradable Pool to IncrementFi will be sent to the black hole address of IncrementFi for locking. That means no one can rug from pulling the LP pool.
* When the LP pool is initially created, coins will be added based on the current price of the Bonding Curve. Therefore, some coins may still be reserved in the Tradable Pool (but continuous deposit will occur later, see [below](./#profit-sharing-and-deflation) section).

_**Built-in Chart**_

* Every transaction conducted on the platform will have a transaction record saved on-chain.
* The built-in Chart uses these transaction records for chart presentation.
* In the future, Dexscreener will also be integrated to provide a more comprehensive UI presentation.

_**Top Holders**_

* In the Tradable Pool, you can see the Top 100 Holders of this coin.
* It is real-time data on-chain, not asynchronous data based on Indexer. The ranking will be automatically updated with each Deposit/Withdrawal.

Note: Only coins that have activated the Tradable module will be included in the global listings on Trending, New, and other exploration pages.

### Profit sharing and Deflation

Transaction fees and inscription costs also be used to automatically re-purchase coins and continuously migrate liquidity for a deflationary boost.

* During the In-Pool phase of trading, the platform will charge a **`0.5%`** transaction fee and also use the Inscription mechanism to clarify the source of **`from`** address.
* Therefore, the potential revenue for each transaction is: **variable** `Transaction Fee` + **fixed** `Inscription Costs`.

The potential income from each transaction will be divided into three parts and deposited into them respectively:

1. `40%` -> The $flows Stakers' Reward Pool (Platform Staking)
2. `30%` -> Platform's contract address (as platform revenue)
3. `30%` -> The coin's contract address (and then will be forwarded to Tradable Pool)

Note: After activating the Tradable Pool, all liquidity($FLOW) deposited to the coin's contract address will be automatically forwarded to the Tradable Pool itself. And the liquidity will have two different functions in two trading stages:

* In-Pool Phase:  it will be automatically added in Market Cap to achieve the target (**$32k**) faster.
* IncrementFi Phase: it will be automatically form a new LP with the reserved coins in Tradable Pool or swap from IncrementFi, and then continue to be burned + added to the SwapPair of IncrementFi. **That means that Coin undergoes continuous deflation and appreciation as transactions increase in this mechanism.**

### Lockdrops and Airdrop

Ordinary users cannot freely adjust the allocation ratio when activating Tradable Pool (i.e., it must be 100%). However, if you are an advanced user of the platform (i.e., staking more than 100k $flows), not only can you reduce the proportion occupied by the Tradable Pool, but you can also use two additional modules: Lockdrops and Airdrops.

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Lockdrops</p></figcaption></figure>

#### _**Lockdrops Module:**_

* Provided a function of locking a specific FT for a period of time to claim coins. The lockable tokens available for the issuer to choose from are $FLOW, $stFLOW, and $fixes.
* The issuer can set the token → coin multiplier by themselves, and this system provides 4 lock-in periods (1 month, 3 months, 6 months, 12 months). The longer the lock-in period, the more coins that can be claimed.
* After the lock-in period expires, users can withdraw the tokens locked in the Lockdrops Pool by themselves.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption><p>Airdrops</p></figcaption></figure>

#### _**Airdrops Module:**_

* Provided a function that allows the issuer to distribute a whitelist address for airdrop, allowing them to claim coins on their own.
* In Settings, each setting action accumulates the Claimable Amount for the configured target whitelist addresses.

Note: The activation of these two modules can only be done when there are still unallocated quotas for the coin. If the coin has been almost fully allocated, it will not be possible to activate them. In the future, new allocation modules may be provided based on platform development.

### Metadata enhanced: DNA system

* Any memecoin created by the platform can be implemented by this system (because of the template contract)
* During buying and selling transactions, FT Vault has a random chance of obtaining DNA genes, with a total of 256 gene fragments, each ranging from quality level 1 to 16.
* Only important operations driven by Inscription will increase the chance of DNA mutation. Once the mutation chance reaches 0, no matter how you manipulate your FT Vault, its DNA cannot mutate again or gain experience.
* DNA provides users’ FT Vault with a certain degree of scarcity and cultivability. It does not have specific functions at present, but it provides on-chain data other than balance.
* **DNA is supposed to be expanded by other composability in the future.**

## &#x20;Guides

{% content-ref url="guide-1-how-to-launch-a-new-coin.md" %}
[guide-1-how-to-launch-a-new-coin.md](guide-1-how-to-launch-a-new-coin.md)
{% endcontent-ref %}
