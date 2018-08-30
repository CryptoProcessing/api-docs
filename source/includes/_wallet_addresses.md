# Wallet addresses

## Wallet address object

> Example

```json
{
    "id": "fa3023cb-e0f1-441c-9e0c-4275e5423691",
    "name": "name",
    "address": "0xcb9b4199021dd923bae7948fb304b5450c2a92e3",
    "final_balance": 100000000000000000,
    "total_received": 100000000000000000,
    "total_sent": 0,
    "txs_count": 1
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
  -H 'Authorization: Token 4d0834297304689f7b7983007775610bdb856c7e15790e7d5c7f857e627fe568' \
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
            "address": "0xcb9b4199021dd923bae7948fb304b5450c2a92e3",
            "final_balance": 100000000000000000,
            "total_received": 100000000000000000,
            "total_sent": 0,
            "txs_count": 1
        },
        {
            "address": "0x910bf3df6d28c06ae9a555aa4b1a6533a2d7aadb",
            "final_balance": 0,
            "total_received": 0,
            "total_sent": 0,
            "txs_count": 0
        },
        {
            "address": "0x5ce2e5deea926f346321167455e476329405528b",
            "final_balance": 0,
            "total_received": 0,
            "total_sent": 0,
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

