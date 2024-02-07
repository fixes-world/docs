# Query Address Trading History

{% swagger method="get" path="/v1/address/:address/frc20/trading-activities?page=0&limit=25&datetime=" baseUrl="http://open-api.fixes.world" summary="Get the trading histories of the given address" fullWidth="true" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter type="Number" in="query" name="page" %}
Start page, default 0
{% endswagger-parameter %}

{% swagger-parameter type="Number" in="query" name="limit" %}
Number of results returned, Up to 100
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="query" name="datetime" type="Number" %}
Timestamp(ms) of the date for the trading history
{% endswagger-parameter %}

{% swagger-parameter in="path" name="address" %}
the given address for querying
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of 𝔉rc20 Trading Histories" %}
```json
{
    "list": [
        {
            "storefront": "0x6de227e6a9c57fdf",
            "buyer": "0x4608754a0c163332",
            "seller": "0x6de227e6a9c57fdf",
            "tick": "flows",
            "dealAmount": 16900,
            "dealPrice": 143.64999884,
            "dealPricePerMint": 0.84999859,
            "timestamp": 1707271860
        },
        {
            "storefront": "0x72572338b801e425",
            "buyer": "0x4608754a0c163332",
            "seller": "0x72572338b801e425",
            "tick": "flows",
            "dealAmount": 10000,
            "dealPrice": 84,
            "dealPricePerMint": 0.84,
            "timestamp": 1707271831
        },
        {
            "storefront": "0x837849d8d1e38f6e",
            "buyer": "0x4608754a0c163332",
            "seller": "0x837849d8d1e38f6e",
            "tick": "flows",
            "dealAmount": 12000,
            "dealPrice": 100.79999966,
            "dealPricePerMint": 0.83999966,
            "timestamp": 1707271806
        },
        {
            "storefront": "0xecb50f2955d00a5c",
            "buyer": "0x4608754a0c163332",
            "seller": "0xecb50f2955d00a5c",
            "tick": "flows",
            "dealAmount": 6000,
            "dealPrice": 49.8,
            "dealPricePerMint": 0.82999966,
            "timestamp": 1707271778
        }
    ]
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="Missing ticker name" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized" %}

{% endswagger-response %}
{% endswagger %}
