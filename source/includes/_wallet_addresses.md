# Wallet addresses

## Wallet address object

> Example

```json
{
    "address": "0x05cb0eab06fbb7ab1aa5708bab3bce35b6bff336",
    "final_balance": "2.189445976325668992",
    "total_received": "2.289446",
    "total_sent": "0.100000023674331008",
    "txs_count": 15
}
```

Represents wallet object
 
### Attributes:

Attribute | Description
--------- | -----------
`id` | Address ID
`name` | Some human name
`address` | Address
`final_balance` | Current address balance 
`total_received` | Incoming transactions amount
`total_sent` | Outgoing transactions amount
`txs_count` | Transactions count 

## Return wallet addresses

> GET https://cryptoprocessing.io/api/v1/wallets/:id/addresses?page=1&limit=25

> Example request

```shell
curl -X GET \
  'https://cryptoprocessing.io/api/v1/wallets/c6136ee4-eabd-4cbe-aed8-ecd0ffdbcc4e/addresses?page=1&limit=25' \
  -H 'Authorization: <jwt token>' \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 3,
        "current_page": 1,
        "last_page": 1,
        "limit": 25,
        "out_of_range": false
    },
    "data": [
        {
            "address": "0x05cb0eab06fbb7ab1aa5708bab3bce35b6bff336",
            "final_balance": "2.189445976325668992",
            "total_received": "2.289446",
            "total_sent": "0.100000023674331008",
            "txs_count": 15
        },
        {
            "address": "0x2a9f57585de532f675660f3ec3f73f41195fa8bb",
            "final_balance": "0.0",
            "total_received": "0.0",
            "total_sent": "0.0",
            "txs_count": 0
        }
    ]
}
```


## Create address

> POST https://cryptoprocessing.io/api/v1/wallets/:id/addresses

### Parameters:

Parameter | Description
--------- | -----------
`name` | Some human name

Returns an address object

