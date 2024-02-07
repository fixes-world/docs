# Get 𝔉rc20 balance

{% swagger method="get" path="/v1/address/:address/frc20/balances/:tick" baseUrl="http://open-api.fixes.world" summary="Get the 𝔉rc20 balance of the given address and given ticker name" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" name="address" required="true" %}
the given address for querying
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tick" required="true" %}
the given ticker name
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="𝔉rc20 balance" %}
```json
{
    "tick": "flows",
    "amount": 10.0
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Invalid address / ticker name" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
