# Fetch 𝔉rc20 Market detailed info

{% swagger method="get" path="/v1/market/:tick" baseUrl="http://open-api.fixes.world" summary="Fetch the detailed 𝔉rc20 Market info of the given tick" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tick" required="true" %}
The ticker name of 𝔉rc20 Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="address" %}
Optionally, add a address in the query, to check whether there are some permissions for the market
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="𝔉rc20 Market Detailed Info" %}
```json
{
    "meta": {
        "tick": "flows",
        "max": 21000000,
        "limit": 100,
        "deployedAt": 1703304138,
        "deployer": "0xa2de93114bae3e73",
        "burnable": false,
        "supplied": 21000000,
        "burned": 0,
        "holders": 2054,
        "poolBalance": 21203.88198416,
        "stakable": true,
        "stakingAddr": "0x17c758477024fa07",
        "marketEnabled": true,
        "isVerified": true
    },
    "volume24h": 378.2499985,
    "sales24h": 4,
    "volumeTotal": 47528.59118265,
    "salesTotal": 714,
    "listedAmount": 109,
    "address": "0xf3a0e19a61defad8",
    "floorPriceBuyListing": 0.0089,
    "ceilingPriceSellListing": 0.008,
    "floorPriceDeal": 0.000025,
    "ceilingPriceDeal": 40500,
    "accessible": true,
    "isValidToClaimAccess": false
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Not found" %}

{% endswagger-response %}
{% endswagger %}
