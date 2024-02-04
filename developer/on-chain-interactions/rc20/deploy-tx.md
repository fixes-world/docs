---
description: Deploy a new 𝔉rc20 token
---

# Deploy - tx

#### Example of Fixes Inscription data string:

```
op=deploy,tick=fixes,max=1000000000.0,limit=1000.0,burnable=1
```

#### Transaction parameters:

<table><thead><tr><th width="116" align="center">Key</th><th width="108" data-type="checkbox">Required</th><th width="100" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">max</td><td>true</td><td align="center">t.UFix64</td><td>Max supply: Set max supply of the 𝔉rc20 token</td></tr><tr><td align="center">limit</td><td>true</td><td align="center">t.UFix64</td><td>Mint limit: limit per inscription</td></tr><tr><td align="center">burnable</td><td>true</td><td align="center">t.Bool</td><td><p>Is this 𝔉rc20 a burnable nscription.</p><p>Recommended to set it as true.</p></td></tr></tbody></table>

#### Transaction code example:

```typescript
import txDeployFRC20 from "@fixes/contracts/transactions/deploy-frc20.cdc?raw";

interface TokenMetaDto {
  tick: string;
  max: number;
  limit: number;
  burnable: boolean;
}

async function deploy(token: TokenMetaDto) {
  return await flow.sendTransaction(txDeployFRC20, (arg, t) => [
      arg(token.tick, t.String),
      arg(token.max.toFixed(8), t.UFix64),
      arg(token.limit.toFixed(8), t.UFix64),
      arg(token.burnable, t.Bool),
  ]);
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/deploy-frc20.cdc" %}

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
* [Check if tick is registered](https://github.com/fixes-world/fixes/blob/main/cadence/scripts/has-tick-registered.cdc)
