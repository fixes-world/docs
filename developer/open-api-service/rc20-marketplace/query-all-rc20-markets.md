# Query all 𝔉rc20 Markets

{% swagger method="get" path="/v1/market" baseUrl="http://open-api.fixes.world" summary="Get the list of all enabled 𝔉rc20 Markets" fullWidth="false" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of 𝔉rc20 Market Basics Info" %}
```json
{
    "list": [
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
            "address": "0xf3a0e19a61defad8"
        },
        {
            "meta": {
                "tick": "worthless",
                "max": 1000000000,
                "limit": 1000000000,
                "deployedAt": 1703990279,
                "deployer": "0xa2de93114bae3e73",
                "burnable": true,
                "supplied": 1000000000,
                "burned": 0,
                "holders": 38,
                "poolBalance": 2.945504,
                "stakable": false,
                "stakingAddr": null,
                "marketEnabled": true,
                "isVerified": true
            },
            "volume24h": 0,
            "sales24h": 0,
            "volumeTotal": 0.918,
            "salesTotal": 4,
            "listedAmount": 6,
            "address": "0x06ef9007881b9df0"
        },
        {
            "meta": {
                "tick": "bitcoin",
                "max": 1000,
                "limit": 2,
                "deployedAt": 1703341136,
                "deployer": "0xeb2d335e7b187a36",
                "burnable": false,
                "supplied": 306,
                "burned": 0,
                "holders": 51,
                "poolBalance": 29.02231,
                "stakable": false,
                "stakingAddr": null,
                "marketEnabled": true,
                "isVerified": false
            },
            "volume24h": 0,
            "sales24h": 0,
            "volumeTotal": 0,
            "salesTotal": 0,
            "listedAmount": 7,
            "address": "0x5efead6d46ec7ec5"
        },
        {
            "meta": {
                "tick": "dragon",
                "max": 21000,
                "limit": 100,
                "deployedAt": 1703341943,
                "deployer": "0x13738c03539ee51d",
                "burnable": false,
                "supplied": 21000,
                "burned": 0,
                "holders": 45,
                "poolBalance": 9.72857,
                "stakable": false,
                "stakingAddr": null,
                "marketEnabled": true,
                "isVerified": false
            },
            "volume24h": 0,
            "sales24h": 0,
            "volumeTotal": 0,
            "salesTotal": 0,
            "listedAmount": 2,
            "address": "0xee62937672b3090f"
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
