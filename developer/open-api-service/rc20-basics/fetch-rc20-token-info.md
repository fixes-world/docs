# Fetch 𝔉rc20 Token Info

{% swagger method="get" path="/v1/frc20/:tick" baseUrl="http://open-api.fixes.world" summary="Get the token info of a 𝔉rc20 FT" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tick" %}
The ticker name of 𝔉rc20 Token
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Object of 𝔉rc20 TokenMeta" %}
```json
{
    "tick": "flows",
    "max": 21000000,
    "limit": 100,
    "deployedAt": 1703304138,
    "deployer": "0xa2de93114bae3e73",
    "burnable": false,
    "supplied": 21000000,
    "burned": 0,
    "holders": 2054,
    "poolBalance": 21198.97441412,
    "stakable": true,
    "stakingAddr": "0x17c758477024fa07",
    "marketEnabled": true,
    "isVerified": true
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Missing ticker" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
