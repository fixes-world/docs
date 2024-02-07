# Estimate Fixes inscribing cost

{% swagger method="get" path="/v1/utils/estimate-cost?text=text-to-inscribe" baseUrl="http://open-api.fixes.world" summary="Estimate the $flow cost for inscribing a new Fixes Inscription" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="query" name="text" %}
The string to inscribe, remember to encodeURIComponent before pass to the API
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="The estimated cost of the given text string" %}
```json
{
    "text": "abcd",
    "cost": 0.2099
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
