# Get 𝔉rc20 balances

## Get the 𝔉rc20 balances of the given address

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/address/:address/frc20/balances?includeFlow=1`

#### Path Parameters

| Name                                      | Type   | Description                    |
| ----------------------------------------- | ------ | ------------------------------ |
| address<mark style="color:red;">\*</mark> | String | the given address for querying |

#### Query Parameters

| Name        | Type | Description                                                      |
| ----------- | ---- | ---------------------------------------------------------------- |
| includeFlow |      | If including Flow Token Balance, "0" means false, "1" means true |

#### Headers

| Name                                            | Type   | Description           |
| ----------------------------------------------- | ------ | --------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Bearer YOUR\_API\_KEY |

{% tabs %}
{% tab title="200: OK 𝔉rc20 balances ("tick"="" means FlowToken)" %}
```json
{
    "address": "0xa2de93114bae3e73",
    "tokens": [
        {
            "tick": "flows",
            "amount": 10.99295469
        },
        {
            "tick": "",
            "amount": 6.67809801
        },
        {
            "tick": "fixes",
            "amount": 1000.00000000
        }
    ]
}
```
{% endtab %}

{% tab title="401: Unauthorized Unauthorized" %}

{% endtab %}

{% tab title="400: Bad Request Invalid address" %}

{% endtab %}
{% endtabs %}
