---
description: List 𝔉rc20 token to the marketplace for sale
---

# List for Sale - tx

#### Example of Fixes Inscription data string:

```
op=list-buynow,tick=fixes,amt=100000.0,price=0.001
```

#### Transaction parameters:

<table><thead><tr><th width="173" align="center">Key</th><th width="99" data-type="checkbox">Required</th><th width="109" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">sellAmount</td><td>true</td><td align="center">t.UFix64</td><td>Amount to sell: States the amount of the 𝔉rc20 token to sell</td></tr><tr><td align="center">sellPrice</td><td>true</td><td align="center">t.UFix64</td><td>Total Price: The total price of selling these 𝔉rc20 tokens.</td></tr><tr><td align="center">commissionAddr</td><td>true</td><td align="center">t.Address</td><td>The address for collecting fees commission splits, 10% of the fees will be sent to this address. (If the listing is not listed in the official market, the original 10% of deployers will be overrided as commission. <a href="https://twitter.com/fixesOnFlow/status/1743141451742208176">learn more</a>)</td></tr><tr><td align="center">customID</td><td>true</td><td align="center">t.String</td><td>The third party market identity (eg. MyMarket)</td></tr></tbody></table>

#### Transaction code example:

```typescript
import txUserListAsBuyNow from "@fixes/contracts/transactions/marketplace/user-list-as-buy-now-with-commission.cdc?raw";

async function userListAsBuyNow(
  tick: string,
  sellAmount: number,
  sellPrice: number,
  commissionAddr: string,
  customID: string,
) {
  const txid = await flow.sendTransaction(txUserListAsBuyNow, (arg, t) => [
    arg(tick, t.String),
    arg(sellAmount.toFixed(8), t.UFix64),
    arg(sellPrice.toFixed(8), t.UFix64),
    arg(commissionAddr, t.Address),
    arg(customID, t.String),
  ]);
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/marketplace/user-list-as-buy-now-with-commission.cdc" %}

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
