# Check 𝔉rc20 registered

{% swagger method="get" path="/v1/frc20/:tick/check-registered" baseUrl="http://open-api.fixes.world" summary="Check if the 𝔉rc20 token has been registered" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tick" %}
The ticker name of 𝔉rc20 Token
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Example Response" %}
```json
{
    "tick": "flows",
    "registered": true
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Missing ticker" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
