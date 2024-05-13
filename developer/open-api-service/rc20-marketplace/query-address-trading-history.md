# Query Address Trading History

## Get the trading histories of the given address

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/address/:address/frc20/trading-activities?page=0&limit=25&datetime=`

#### Path Parameters

| Name    | Type   | Description                    |
| ------- | ------ | ------------------------------ |
| address | String | the given address for querying |

#### Query Parameters

| Name     | Type   | Description                                       |
| -------- | ------ | ------------------------------------------------- |
| page     | Number | Start page, default 0                             |
| limit    | Number | Number of results returned, Up to 100             |
| datetime | Number | Timestamp(ms) of the date for the trading history |

#### Headers

| Name                                            | Type   | Description           |
| ----------------------------------------------- | ------ | --------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Bearer YOUR\_API\_KEY |

{% tabs %}
{% tab title="200: OK List of 𝔉rc20 Trading Histories" %}
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
{% endtab %}

{% tab title="401: Unauthorized Unauthorized" %}

{% endtab %}

{% tab title="400: Bad Request Missing ticker name" %}

{% endtab %}
{% endtabs %}
