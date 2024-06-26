---
description: Get all fungible tokens
---

# 📘 Query TokenList

#### **Mainnet**

<mark style="color:green;">`GET`</mark> _https://token-list.fixes.world/api/token-list\[/:reviewer]\[?filter=]\[\&page=]\[\&limit=]_

#### **Testnet**

<mark style="color:green;">`GET`</mark> _https://testnet-token-list.fixes.world/api/token-list\[/:reviewer]\[?filter=]\[\&page=]\[\&limit=]_

#### **Parameter**

<table><thead><tr><th width="137">Name</th><th width="105">Type</th><th width="107">Default</th><th>Description</th></tr></thead><tbody><tr><td><code>reviewer</code></td><td>Address</td><td>undefined</td><td>When no Reviewer is set, the default list will be returned. If a reviewer is set, the data customized by the reviewer will be returned.</td></tr></tbody></table>

#### **Query**

<table><thead><tr><th width="135">Name</th><th width="107">Type</th><th width="109">Default</th><th>Description</th></tr></thead><tbody><tr><td><code>filter</code></td><td>Number</td><td>0</td><td><pre><code>0 - All
1 - Reviewed by Reviewer
2 - Managed by Reviewer
3 - Verified by Reviewer
4 - Featured by Reviewer
</code></pre></td></tr><tr><td><code>page</code></td><td>Number</td><td>undefined</td><td>If set, use Pagination; otherwise, retrieve all.</td></tr><tr><td><code>limit</code></td><td>Number</td><td>undefined</td><td>If set, use Pagination; otherwise, retrieve all.</td></tr></tbody></table>

#### **Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "name": "Flow Token List",
  "tokens": [
    {
      "address": "0xf8d6e0586b0a20c7",
      "contractName": "ExampleToken",
      "path": {
        "vault": "/storage/exampleTokenVault",
        "receiver": "/public/exampleTokenReceiver",
        "balance": "/public/exampleTokenMetadata"
      },
      "symbol": "EFT",
      "name": "Example Fungible Token",
      "description": "Hello World1\nThis fungible token is used as an example to help you develop your next FT #onFlow.",
      "decimals": 8,
      "logoURI": "https://assets.website-files.com/5f6294c0c7a8cdd643b1c820/5f6294c0c7a8cda55cb1c936_Flow_Wordmark.svg",
      "tags": [],
      "extensions": {
        "twitter": "https://twitter.com/flow_blockchain",
        "website": "https://example-ft.onflow.org",
        "displaySource": "0x179b6b1cb6755e31"
      }
    }
  ],
  "totalAmount": 1,
  "filterType": "ALL",
  "timestamp": "2024-04-18T13:28:20.423Z",
  "logoURI": "https://cdn.jsdelivr.net/gh/FlowFans/flow-token-list@main/token-registry/A.1654653399040a61.FlowToken/logo.svg",
  "keywords": [
    "Flow",
    "Cadence",
    "EVM",
    "DeFi",
    "NFT",
    "FT",
    "Dapp",
    "Blockchain",
    "Crypto"
  ],
  "tags": {
    "stablecoin": {
      "name": "stablecoin",
      "description": "Tokens that are fixed to an external asset, e.g. the US dollar"
    },
    "ethereum": {
      "name": "ethereum",
      "description": "Asset bridged from ethereum"
    },
    "wrapped-celer": {
      "name": "wrapped-celer",
      "description": "Asset wrapped using celer bridge"
    },
    "lp-token": {
      "name": "lp-token",
      "description": "Asset representing liquidity provider token"
    },
    "utility-token": {
      "name": "utility-token",
      "description": "Tokens that are designed to be spent within a certain blockchain ecosystem"
    },
    "governance-token": {
      "name": "governance-token",
      "description": "Tokens that are designed to be use in community governance and maintenance"
    },
    "memecoin": {
      "name": "memecoin",
      "description": "Tokens that are created for fun and meme"
    }
  },
  "version": {
    "major": 1,
    "minor": 0,
    "patch": 0
  }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "success": false,
    "error": {
        "message": "The reviewer address is invalid"
    }
}
```
{% endtab %}
{% endtabs %}
