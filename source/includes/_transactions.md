# Transactions

## The transaction object


Parameter             | Description
---------             | ---------
`id`                  | Transaction id
`tx_hash`             | Transaction hash
`fromaddress`         | A ethereum address of the sender
`toaddress`           | A ethereum address of the recipient
`gasprice`            | Gas price
`block_number`        | Block number where the transaction is included
`confirmations_count` | Transaction confirmation count
`description`         | Transaction description
`data`                | Ethereum transaction data 
`nonce`               | Ethereum transaction nonce
`type`                | Transaction type
`value`               | Transaction amount 
`statuses`            | Array of transaction statuses


## Get All Transactions

```shell
curl "http://example.com/api/transactions"
  -H "Authorization: <jwt token>"
```

> The above command returns JSON structured like this:

```json
{
    "transactions": [
        {
            "block_number": 3044794,
            "confirmations_count": 5353,
            "data": "0x",
            "description": "Incoming transaction",
            "fromaddress": "0x687422eEA2cB73B5d3e242bA5456b782919AFc85",
            "gasprice": 18000000000,
            "id": 1,
            "nonce": 460724,
            "toaddress": "0xb8bdedee86f701da8ef631750a964dbbe8802c7a",
            "tx_hash": "0x7a17815610b26c84baccab514460175f67549272cd8afb1dae2b4a7d419741ba",
            "type": "receive",
            "value": 1000000000000000000,
            "statuses": [
                        {
                            "date": "Sun, 15 Apr 2018 19:39:32 GMT",
                            "status": "in mempool"
                        },
                        {
                            "date": "Sun, 15 Apr 2018 19:40:18 GMT",
                            "status": "in block"
                        }
                   ]
        },
        {
            "block_number": 3045065,
            "confirmations_count": 5082,
            "data": "0x00",
            "description": "Incoming transaction",
            "fromaddress": "0xe17F97b518E9E8bBC9b72Ab88fd3f9db10BeA981",
            "gasprice": 10000000000,
            "id": 2,
            "nonce": 5913,
            "toaddress": "0xb8bdedee86f701da8ef631750a964dbbe8802c7a",
            "tx_hash": "0x48236cf22901c805c582b0db5437c7eee79741578dc364f2110b25538374d60c",
            "type": "receive",
            "value": 1000000000000000000,
            "statuses": [
                        {
                            "date": "Sun, 15 Apr 2018 20:34:53 GMT",
                            "status": "in mempool"
                        },
                        {
                            "date": "Sun, 15 Apr 2018 20:34:55 GMT",
                            "status": "in block"
                        }
                    ]
        }
    ]
}
```

This endpoint retrieves all transactions.

### HTTP Request

`GET http://example.com/api/transactions`

### Query Parameters


<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Create A Transaction

```shell
curl -X POST "http://example.com/api/transactions"
  -H "Authorization: <jwt token>"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all transactions.

### HTTP Request

`POST http://example.com/api/transactions`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>
