# Get 𝔉rc20 balances

{% swagger method="get" path="/v1/address/:address/frc20/balances?includeFlow=1" baseUrl="http://open-api.fixes.world" summary="Get the 𝔉rc20 balances of the given address" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="query" name="includeFlow" type="" %}
If including Flow Token Balance, "0" means false, "1" means true
{% endswagger-parameter %}

{% swagger-parameter in="path" name="address" required="true" %}
the given address for querying
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="𝔉rc20 balances ("tick"="" means FlowToken)" %}
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
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid address" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
