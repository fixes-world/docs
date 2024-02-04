---
description: Mint 𝔉rc20 token
---

# Mint(batch) - tx

#### Example of Fixes Inscription data string:

```
op=mint,tick=fixes,amt=1000.0
```

#### Transaction parameters:

<table><thead><tr><th width="116" align="center">Key</th><th width="108" data-type="checkbox">Required</th><th width="100" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">amt</td><td>true</td><td align="center">t.UFix64</td><td>Amount to mint: States the amount of the 𝔉rc20 token to mint. Has to be less or equal to "limit" </td></tr><tr><td align="center">repeats</td><td>true</td><td align="center">t.UInt64</td><td>How many times to repeat the mint action. Better less than or equal to 100 times.</td></tr></tbody></table>

#### Transaction code example:

```typescript
import txBatchMintFRC20 from "@fixes/contracts/transactions/batch-mint-frc20.cdc?raw";
import txMintFRC20 from "@fixes/contracts/transactions/mint-frc20.cdc?raw";

async function mint(
  tick: string,
  amt: number,
  repeats: number = 1
) {
  let txid: string;
  if (repeats > 1) {
    txid = await flow.sendTransaction(txBatchMintFRC20, (arg, t) => [
      arg(tick, t.String),
      arg(amt.toFixed(8), t.UFix64),
      arg(repeats, t.UInt64),
    ]);
  } else {
    txid = await flow.sendTransaction(txMintFRC20, (arg, t) => [
      arg(tick, t.String),
      arg(amt.toFixed(8), t.UFix64),
    ]);
  }
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/batch-mint-frc20.cdc" %}

Or mint simple inscription

[https://github.com/fixes-world/fixes/blob/main/cadence/transactions/mint-frc20.cdc](https://github.com/fixes-world/fixes/blob/main/cadence/transactions/mint-frc20.cdc)

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
