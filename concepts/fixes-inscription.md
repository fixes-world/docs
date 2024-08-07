---
description: Fixes - the inscription contract of the FIXeS protocol.
---

# 🔡 Fixes Inscription

{% hint style="info" %}
The data structure of Fixes inscription is referenced from [Ordinals](https://docs.ordinals.com/inscriptions.html#fields).
{% endhint %}

## What is the core concept of the Fixes Inscription?

Flow is different from other public chains in that its transactions must be executable transaction scripts, which themselves have very strong computational capabilities. Therefore, we choose not to blindly reference the implementation methods of other public chains, but instead try to find the essence of why we need inscription and the inscription protocol from first principles.

For Ordinals, the two key features of their inscription are:&#x20;

* One is to directly store any data in bytecode on the chain
* Another is that the `UTXO` containing the inscription itself has value (holds real `$BTC`)

So we decided to follow these two features when designing the inscription.

* We need to encapsulate arbitrary data in the form of `[UInt8]` and store it on-chain as an inscription resource (Actually, this is the basic functionality of the Flow blockchain.).
* We also want to store a certain amount of `$FLOW` in the inscription resource.

## Why and How to Store $FLOW in the Fixes inscription?

Because we need to make the inscriptions themselves valuable, and for FIXeS, the inscriptions can only be stored in users' accounts. And when you need to extract and use these `$FLOW` reasonably in the corresponding application protocol for FIXeS inscriptions (Like 𝔉rc20 Indexer).

As for how to store, thanks to [Cadence's resource mechanism](https://cadence-lang.org/docs/language/resources). Flow Tokens naturally be composable. Just extract a certain amount of `$FLOW` and store it in the Inscription resource.

## How will these $FLOW be used?

Different application protocols based on the FIXeS protocol, can have completely different usage methods.

> For 𝔉rc20 Indexer

* When each inscription is applied by the 𝔉rc20 Indexer,  `$FLOW` will be extracted to the Token's Treasury Pool (5% will also be extracted to the global pool of the 𝔉rc20 Indexer).
* When the 𝔉rc20 token is burnable, 𝔉rc20 token holders can withdraw a certain amount of `$FLOW` from the Treasury Pool through the `burn` op corresponding to the burned amount.

More details can be found in [rc20s.md](rc20s.md "mention").

> For any Fixes Coins

* The $FLOW inside key operation inscription will be extracted when the  operation is performed.  They will be transferred to three targets:&#x20;
  * **40%** to the $flows stakers as staking reward
  * **30%** to the Coins' contract address (If Tradable pool is activatd, It will be deposited into the $FLOW Vault of the Tradable Pool.)
  * **30%** to the platform contact address.

More details can be found in [fixes-coins](fixes-coins/ "mention")

## Can I use Fixes Inscription for my project?

Of course, the Fixes is a completely open protocol that you can use to build any application based on the Inscriptions.

## Are the contracts open-sourced? <a href="#contracts" id="contracts"></a>

Yes, you can find all contracts here

| Network | Contract Address                                                                       |
| ------- | -------------------------------------------------------------------------------------- |
| Mainnet | [0xd2abb5dbf5e08666](https://contractbrowser.com/account/0xd2abb5dbf5e08666/contracts) |
| Testnet | [0xb7248baa24a95c3f](https://contractbrowser.com/account/0xb7248baa24a95c3f/contracts) |

