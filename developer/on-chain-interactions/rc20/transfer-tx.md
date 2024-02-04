---
description: Transfer 𝔉rc20 token
---

# Transfer - tx

#### Example of Fixes Inscription data string:

```
op=transfer,tick=fixes,amt=100000.0,to=0xd2abb5dbf5e08666
```

#### Transaction parameters:

<table><thead><tr><th width="116" align="center">Key</th><th width="108" data-type="checkbox">Required</th><th width="106" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">amt</td><td>true</td><td align="center">t.UFix64</td><td>Amount to transfer: States the amount of the 𝔉rc20 to transfer.</td></tr><tr><td align="center">to</td><td>true</td><td align="center">t.Address</td><td>The recipient of 𝔉rc20 tokens.</td></tr></tbody></table>

#### Transaction code example:

```typescript
import txTransferFRC20 from "@fixes/contracts/transactions/transfer-frc20.cdc?raw";

async function transferFRC20(
  tick: string,
  to: string,
  amt: number
) {
  const txid = await flow.sendTransaction(txTransferFRC20, (arg, t) => [
    arg(tick, t.String),
    arg(amt.toFixed(8), t.UFix64),
    arg(to, t.Address),
  ]);
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/transfer-frc20.cdc" %}

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
