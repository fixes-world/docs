# Get current $FLOW price

{% swagger method="get" path="/v1/utils/estimate-cost?text=text-to-inscribe" baseUrl="http://open-api.fixes.world" summary="Get current $FLOW price (In USD, using IncrementFi price oracle) " fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="price result" %}
```json
{
    "price": 0.73390062
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
