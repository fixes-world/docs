---
description: Marketenabled
---

# Check 𝔉rc20 Market enabled

## Check if the 𝔉rc20 market has been enabled

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/market/:tick/check-enabled`

#### Path Parameters

| Name                                   | Type   | Description                     |
| -------------------------------------- | ------ | ------------------------------- |
| tick<mark style="color:red;">\*</mark> | String | The ticker name of 𝔉rc20 Token |

#### Headers

| Name                                            | Type   | Description           |
| ----------------------------------------------- | ------ | --------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Bearer YOUR\_API\_KEY |

{% tabs %}
{% tab title="200: OK Example Response" %}
```json
{
    "tick": "flows",
    "marketEnabled": true
}
```
{% endtab %}

{% tab title="401: Unauthorized Unauthorized" %}

{% endtab %}

{% tab title="400: Bad Request Missing ticker" %}

{% endtab %}
{% endtabs %}
