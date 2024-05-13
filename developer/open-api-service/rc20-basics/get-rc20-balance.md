# Get 𝔉rc20 balance

## Get the 𝔉rc20 balance of the given address and given ticker name

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/address/:address/frc20/balances/:tick`

#### Path Parameters

| Name                                      | Type   | Description                    |
| ----------------------------------------- | ------ | ------------------------------ |
| address<mark style="color:red;">\*</mark> | String | the given address for querying |
| tick<mark style="color:red;">\*</mark>    | String | the given ticker name          |

#### Headers

| Name                                            | Type   | Description           |
| ----------------------------------------------- | ------ | --------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Bearer YOUR\_API\_KEY |

{% tabs %}
{% tab title="200: OK 𝔉rc20 balance" %}
```json
{
    "tick": "flows",
    "amount": 10.0
}
```
{% endtab %}

{% tab title="401: Unauthorized Unauthorized" %}

{% endtab %}

{% tab title="400: Bad Request Invalid address / ticker name" %}

{% endtab %}
{% endtabs %}
