---
description: Take the 𝔉rc20 token sale listing as a buyer
---

# Take list as buyer  - tx

#### Example of Fixes Inscription data string:

```
op=list-take-buynow,tick=fixes,amt=10000.0
```

#### Transaction parameters:

<table><thead><tr><th width="161" align="center">Key</th><th width="102" data-type="checkbox">Required</th><th width="169" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">tick</td><td>true</td><td align="center">t.String</td><td>Ticker: identity of the 𝔉rc20 token</td></tr><tr><td align="center">batchBuyItems</td><td>true</td><td align="center">t.Dictionary({ key: t.String, value: t.UFix64 })</td><td><p>The dictionary for buying:</p><p><code>rankedId => Amount</code> <br>You can get RankedListingId by querying the marketplace</p></td></tr></tbody></table>

:notebook:**Note:** The key of `batchBuyItems` should be `itemInMarket.rankedId` which can be obtained in the response of querying listings. and the value is how much tokens you will take in the order. **𝔉rc20 trading orders support partial deal.**

#### Transaction code example:

```typescript
import txUserTakeAsBuyer from "@fixes/contracts/transactions/marketplace/user-take-as-buyer-with-commission.cdc?raw";

async function userTakeAsBuyer(
  tick: string,
  batchBuyItems: Record<string, number>
) {
  let args: Array<{ key: string; value: string }> = [];
  for (const key in batchBuyItems) {
    if (!Object.prototype.hasOwnProperty.call(batchBuyItems, key)) continue;
    args.push({
      key,
      value: batchBuyItems[key].toFixed(8),
    });
  }
  const txid = await flow.sendTransaction(txUserTakeAsBuyer, (arg, t) => [
    arg(tick, t.String),
    arg(args, t.Dictionary({ key: t.String, value: t.UFix64 })),
  ]);
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/marketplace/user-take-as-buyer-with-commission.cdc" %}

#### Related docs

* [estimatecost-read.md](../fixes-inscription/estimatecost-read.md "mention")
* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
* [query-rc20-listings.md](../../open-api-service/rc20-marketplace/query-rc20-listings.md "mention")
