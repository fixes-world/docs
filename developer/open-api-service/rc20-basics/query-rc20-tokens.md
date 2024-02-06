# Query 𝔉rc20 Tokens

{% swagger method="get" path="/v1/frc20?page=0&limit=30" baseUrl="http://open-api.fixes.world" summary="Get the list of all 𝔉rc20 FTs" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="page" %}
Start page, default 0
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" %}
Number of tokens returned, Up to 100
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of TokenMeta" %}
```json
{
  "list": [
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
    },
    {
      "tick": "wolf",
      "max": 1000000,
      "limit": 1000,
      "deployedAt": 1703340393,
      "deployer": "0xb9bb9404767cd896",
      "burnable": true,
      "supplied": 1000000,
      "burned": 1000,
      "holders": 126,
      "poolBalance": 199.38704598,
      "stakable": false,
      "stakingAddr": null,
      "marketEnabled": false,
      "isVerified": false
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
