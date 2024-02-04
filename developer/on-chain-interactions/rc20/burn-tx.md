---
description: Burn 𝔉rc20 token (only for burnable 𝔉rc20)
---

# Burn - tx

#### Example of Fixes Inscription data string:

```
op=burn,tick=fixes,amt=100000.0
```

#### Transaction parameters:

<table><thead><tr><th width="116" align="center">Key</th><th width="108" data-type="checkbox">Required</th><th width="100" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">amt</td><td>true</td><td align="center">t.UFix64</td><td>Amount to burn: States the amount of the 𝔉rc20 token to burn</td></tr></tbody></table>

#### Transaction code example:

```typescript
import txBurnFRC20 from "@fixes/contracts/transactions/burn-frc20.cdc?raw";

export async function burnFRC20(
  tick: string,
  amt: number
) {
  const txid = await flow.sendTransaction(txBurnFRC20, (arg, t) => [
    arg(tick, t.String),
    arg(amt.toFixed(8), t.UFix64),
  ]);
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/burn-frc20.cdc" %}

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
