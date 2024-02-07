# Query 𝔉rc20 Listings

{% swagger method="get" path="/v1/market/:tick/listings?type=0&limit=25&startPriceRank=&startPriceRankIdx=" baseUrl="http://open-api.fixes.world" summary="Get the list of 𝔉rc20 trading listings in the given market" fullWidth="true" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
Bearer YOUR\_API\_KEY
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="tick" %}
The ticker name of 𝔉rc20 Token
{% endswagger-parameter %}

{% swagger-parameter in="query" name="type" required="false" type=""0" | "1"" %}
The listing type, "0" means orders for sale (You can display as buyNow), "1" means orders for purchase (You can display as sellNow), Default: “0”
{% endswagger-parameter %}

{% swagger-parameter in="query" name="limit" type="Number" %}
Number of results returned, Up to 100
{% endswagger-parameter %}

{% swagger-parameter in="query" name="startPriceRank" type="Number" %}
Query start from the given **priceRank**, you can get the priceRank in the previous response. Default: undefined
{% endswagger-parameter %}

{% swagger-parameter in="query" name="startPriceRankIdx" type="Number" %}
Query start from the given **priceRankIdx**, you can get the rankedIdx in the previous response. Default: undefined
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="List of Listing Orders" %}
```json
{
    "list": [
        {
            "type": 0,
            "priceRank": 890,
            "rankedIdx": 0,
            "itemInMarket": {
                "rankedId": "0-890-1472995729",
                "storefront": "0x936c354755d0b2d9",
                "listingId": "1472995729",
                "timestamp": 1707068329
            },
            "details": {
                "storefrontId": "1440492416",
                "inscriptionId": "1398851",
                "type": 0,
                "tick": "flows",
                "amount": 5000,
                "transactedAmount": 0,
                "totalPrice": 44.5,
                "priceValuePerMint": 0.89,
                "createdAt": 1707068329,
                "status": 0,
                "customID": null
            }
        },
        {
            "type": 0,
            "priceRank": 899,
            "rankedIdx": 0,
            "itemInMarket": {
                "rankedId": "0-899-1456703409",
                "storefront": "0xcf214661ef31cbe2",
                "listingId": "1456703409",
                "timestamp": 1706192323
            },
            "details": {
                "storefrontId": "1456703406",
                "inscriptionId": "1133689",
                "type": 0,
                "tick": "flows",
                "amount": 69000,
                "transactedAmount": 8511,
                "totalPrice": 621,
                "priceValuePerMint": 0.9,
                "createdAt": 1706192323,
                "status": 0,
                "customID": null
            }
        },
        {
            "type": 0,
            "priceRank": 930,
            "rankedIdx": 0,
            "itemInMarket": {
                "rankedId": "0-930-1466118910",
                "storefront": "0x936c354755d0b2d9",
                "listingId": "1466118910",
                "timestamp": 1706685218
            },
            "details": {
                "storefrontId": "1440492416",
                "inscriptionId": "1305790",
                "type": 0,
                "tick": "flows",
                "amount": 4000,
                "transactedAmount": 0,
                "totalPrice": 37.2,
                "priceValuePerMint": 0.93,
                "createdAt": 1706685218,
                "status": 0,
                "customID": null
            }
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
