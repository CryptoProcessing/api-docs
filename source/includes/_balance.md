# Balance

## The balance object

> Example

```json
{
  "date": "2018-04-10T14:48:00.000Z",
  "balance": [
    {
      "currency": "BTC",
      "total": 123,
      "wallets": [
        { 
          "wallet": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
          "total": 100 
        },
        {
          "wallet": "3QJmV3qfvL9SuYo34YihAf3sRCW3qSinyC",
          "total": 23
        }
      ]
    },
    {
      "currency": "ETH",
      "total": 321,
      "wallets": [
        {
          "wallet": "0xe99356bde974bbe08721d77712168fa070aa8da4",
          "total": 321
        }
      ]
    }
  ]
}
```
 
### Attributes:

Attribute | Description
--------- | -----------
`data` | Balance date
`balance` | Array of balance currencies
`currency` | Currency
`total` | Currency total amount
`wallets` | Array of selected currency wallets
`wallet` | Wallet hash id


## Get balance

```shell
curl "http://example.com/api/balance?currency=BTC"
  -H "Authorization: <jwt token>"
```

> The above command returns JSON structured like this:

```json
{
  "date": "2018-04-10T14:48:00.000Z",
  "balance": [
    {
      "currency": "BTC",
      "total": 123,      
      "wallets": [
        { 
          "wallet": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
          "total": 100 
        },
        {
          "wallet": "3QJmV3qfvL9SuYo34YihAf3sRCW3qSinyC",
          "total": 23
        }
      ]
    }
  ]
}

```

This endpoint, retrieves currency balance

### Filter parameters

Parameter | Default |Description
--------- | ------- | -----------
`currency` | empty | Filter by currency
`to_date` | empty | Balance to date
`including_empty` | false | Balance will be returned with zero balanced wallets.



