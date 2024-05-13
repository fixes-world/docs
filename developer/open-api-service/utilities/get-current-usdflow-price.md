# Get current $FLOW price

## Get current $FLOW price (In USD, using IncrementFi price oracle)&#x20;

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/utils/estimate-cost?text=text-to-inscribe`

#### Headers

| Name                                            | Type   | Description           |
| ----------------------------------------------- | ------ | --------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Bearer YOUR\_API\_KEY |

{% tabs %}
{% tab title="200: OK price result" %}
```json
{
    "price": 0.73390062
}
```
{% endtab %}

{% tab title="401: Unauthorized Unauthorized" %}

{% endtab %}
{% endtabs %}
