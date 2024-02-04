---
description: Cancel a 𝔉rc20 token listing
---

# Cancel Listing - tx

This transaction does not need to inscribe, so it does not include the cost of inscriptions.

#### Transaction parameters:

<table><thead><tr><th width="173" align="center">Key</th><th width="99" data-type="checkbox">Required</th><th width="109" align="center">FType</th><th>Description</th></tr></thead><tbody><tr><td align="center">listingId</td><td>true</td><td align="center">t.UInt64</td><td>ListingID: the unique listing id in user's storefront. <br>You can get the listingId by querying the marketplace</td></tr></tbody></table>

#### Transaction code example:

```typescript
import txUserCancelListing from "@fixes/contracts/transactions/marketplace/user-cancel-listing.cdc?raw";

async function userCancelListing(
  listingId: string
) {
  const txid = await flow.sendTransaction(txUserCancelListing, (arg, t) => [
    arg(listingId, t.UInt64),
  ]);
  return txid;
}
```

#### Transaction source code

{% @github-files/github-code-block url="https://github.com/fixes-world/fixes/blob/main/cadence/transactions/marketplace/user-cancel-listing.cdc" %}

#### Related docs

* [#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain](../#how-to-send-a-transaction-to-flow-blockchain-or-query-data-from-flow-blockchain "mention")
