# Query Market Trading History

## Get the trading histories of the given 𝔉rc20 market

<mark style="color:blue;">`GET`</mark> `http://open-api.fixes.world/v1/market/:tick/trading-activites?page=0&limit=25&datetime=`

#### Path Parameters

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| tick | String | The ticker name of 𝔉rc20 Token |

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
        },
        {
            "storefront": "0x36684bae2906081a",
            "buyer": "0x36684bae2906081a",
            "seller": "0xe5cb1a35821237c7",
            "tick": "flows",
            "dealAmount": 1500,
            "dealPrice": 10.65,
            "dealPricePerMint": 0.70999992,
            "timestamp": 1707203042
        },
        {
            "storefront": "0xecb50f2955d00a5c",
            "buyer": "0xecb50f2955d00a5c",
            "seller": "0xe5cb1a35821237c7",
            "tick": "flows",
            "dealAmount": 3000,
            "dealPrice": 22.5,
            "dealPricePerMint": 0.74999992,
            "timestamp": 1707202630
        },
        {
            "storefront": "0x837849d8d1e38f6e",
            "buyer": "0xa2de93114bae3e73",
            "seller": "0x837849d8d1e38f6e",
            "tick": "flows",
            "dealAmount": 1000,
            "dealPrice": 8.39999924,
            "dealPricePerMint": 0.83999992,
            "timestamp": 1707187320
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
