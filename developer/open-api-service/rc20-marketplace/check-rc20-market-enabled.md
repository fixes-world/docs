---
description: Marketenabled
---

# Check 𝔉rc20 Market enabled

{% swagger method="get" path="/v1/market/:tick/check-enabled" baseUrl="http://open-api.fixes.world" summary="Check if the 𝔉rc20 market has been enabled" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tick" required="true" %}
The ticker name of 𝔉rc20 Token
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Example Response" %}
```json
{
    "tick": "flows",
    "marketEnabled": true
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Missing ticker" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
