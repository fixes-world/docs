---
description: Get all reviewers
---

# 📙 Query Reviewers

#### **Mainnet**

<mark style="color:green;">`GET`</mark> _https://token-list.fixes.world/api/reviewers_

#### **Testnet**

<mark style="color:green;">`GET`</mark> _https://testnet-token-list.fixes.world/api/reviewers_

#### **Parameter**

None

#### **Query**

None

#### **Response**

{% tabs %}
{% tab title="200" %}
```json
[
    {
        "address": "0xa2de93114bae3e73",
        "verified": true,
        "name": "Fixes World",
        "url": "https://linktr.ee/fixes.world",
        "managedTokenAmt": 30,
        "reviewedTokenAmt": 45,
        "customziedTokenAmt": 36
    }
]
```
{% endtab %}

{% tab title="400" %}
```json
{
    "success": false,
    "error": {
        "message": ""
    }
}
```
{% endtab %}
{% endtabs %}
