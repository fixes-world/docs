---
description: >-
  An experimental application protocol of FIXeS. The on-chain 𝔉rc20 token
  indexer and maintainer.
---

# 𝔉rc20 Indexer

FRC20Indexer is an on-chain Indexer based on the FIXeS inscription protocol, which is used to parse and utilize 𝔉rc20 tokens recorded in FIXeS inscription.

At the same time, it also provides support for the Treasury Pool for 𝔉rc20 Tokens, allowing the token value of frc20 to naturally increase during any operation regarding the token.

## 𝔉rc20 Token Modes

𝔉rc20 Indexer offers two types of tokens:

* a standard mode that follows the [BRC-20 protocol](https://domo-2.gitbook.io/brc-20-experiment/)
* a burnable mode that allows `burn` operation by holders.

## How will the 𝔉rc20 Indexer handle $FLOW in the inscription?

* All operations performed on the 𝔉rc20 Indexer application Inscription will extract `$FLOW` to the corresponding Token Treasury Pool.
  * `5%` of them will be extracted to the Platform Pool of 𝔉rc20 Indexer, which will provide certain support for FIXeS operational activities and cover development expenses.
* For burnable 𝔉rc20 Tokens, when the holder applies an 𝔉rc20 inscription containing a `burn` operation, the corresponding `$FLOW` tokens can be extracted from the Treasury Pool.
* When an 𝔉rc20 token is injected into the liquidity pool in the form of staking (TBD), the Treasury Pool (:construction:Still WIP) will also help provide liquidity.

## 𝔉rc20 Treasury Pool

Indexer manages: **Treasury Pool** and **Liquidity Pool(TBD)**

* Treasury Pool - Each 𝔉rc20 Token has its own Treasury Pool, and when any 𝔉rc20 Inscription is applied, the internal `$FLOW` will be automatically injected into this pool.
* Liquidity Pool(TBD) - 𝔉rc20 Token can form a trading pair with `$FLOW` Token and be added to the liquidity pool for users to swap. When the 𝔉rc20 Token is injected into the liquidity pool as staking mode, the Treasury Pool will automatically contribute a certain amount of `$FLOW` Token to provide liquidity.

## 𝔉rc20 Marketplace

> Marketplace is launched: [https://fixes.world/marketplace](https://fixes.world/marketplace)

Check out the intro of FIXeS Marketplace:

{% embed url="https://twitter.com/fixesOnFlow/status/1743141443294880155" %}
