# Wallet's address transactions 


## The ETH transaction object


Parameter             | Description
---------             | ---------
`hash`                | Transaction hash
`block_number`        | Block number where the transaction is included
`confirmations_count` | Transaction confirmation count
`description`         | Transaction description
`gasprice`            | Gas price
`gaslimit`            | Gas limit
`nonce`               | Ethereum transaction nonce
`type`                | Transaction type
`value`               | Transaction amount
`sender_address`      | A ethereum address of the sender
`receiver_address`    | A ethereum address of the recipient
`statuses`            | Array of transaction statuses


## The BTC transaction object


Parameter             | Description
---------             | ---------
`hash`                | Transaction hash
`amount`              | Transaction amount
`block_number`        | Block number where the transaction is included
`confirmations_count` | Transaction confirmation count
`fee`                 | Transaction fee
`type`                | Transaction type
`description`         | Transaction description
`receiver_addresses`  | Array of receiver addresses with amount
`sender_address`      | Array of sender addresses with amount
`statuses`            | Array of transaction statuses


## Get All Transactions

Parameter             | Description
---------             | ---------
`wallet_id`           | Wallet ID
`address   `          | Address
`from_date`           | From date
`to_date`             | Before date
`page`                | Pagination starts at page 1, not at page 0 (page 0 will return the same results as page 1)
`limit`               | A limit on the number if objects to be returned. (default 25, max 100)
`fromaddress`         | Sender address
`toaddress`           | Receiver address


> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions

```shell
curl "https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions?
&from_date=2016-04-12T00:00:00.000Z&to_date=2019-04-30T00:00:00.01100Z&page=1&limit=10&fromaddress&toaddress
  -H "Authorization: Token <token>"
```

> For the Ethereum the above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 1,
        "current_page": 1,
        "last_page": 1,
        "limit": 10,
        "out_of_range": false
    },
    "data": [
        {
            "hash": "0x03c3885a9885794cfea15d5b49f53c3d8d1afe7cf6107581e60b043b7d9a9288",
            "block_number": 4124533,
            "confirmations_count": 664,
            "description": "Incoming transaction",
            "gasprice": 1000000000,
            "gaslimit": 21000,
            "nonce": 91,
            "type": "receive",
            "value": 100000000000000000,
            "sender_address": "0x8abAb4093391340180CACe15404866499bb7D701",
            "receiver_address": "0x05cb0eab06fbb7ab1aa5708bab3bce35b6bff336",
            "statuses": [
                {
                    "status": "in mempool",
                    "date": "Thu, 27 Sep 2018 13:02:46 GMT"
                },
                {
                    "status": "in block",
                    "date": "Thu, 27 Sep 2018 13:03:28 GMT"
                }
            ]
        }
    ]
}
```
> For the Bitcoin the above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 1,
        "current_page": 1,
        "last_page": 1,
        "limit": 10,
        "out_of_range": false
    },
    "data": [
        {
            "hash": "0e43f55fc601d5fcb6f6469fb8454e2dc807306d1166c0d31e096a824c5a807d",
            "amount": 2000000,
            "block_number": null,
            "confirmations_count": 0,
            "fee": null,
            "type": "receive",
            "description": "Incoming transaction",
            "receiver_addresses": [
                {
                    "address": "my3h9MQKDdks9nMqcStKu58yMrz8uVucW5",
                    "amount": 82705141
                },
                {
                    "address": "2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv",
                    "amount": 2000000
                }
            ],
            "sender_addresses": [
                {
                    "address": "n12CTVJYj5ecLYYH9wZiyyV7frVx1E7K9L"
                }
            ],
            "statuses": [
                {
                    "status": "in mempool",
                    "date": "Thu, 27 Sep 2018 13:42:35 GMT"
                }
            ]
        }
    ]
}
```


## Create A Transaction

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions

```shell
curl -X POST "https://cryptoprocessing.io/api/v1/wallets/:id/transactions"
 -d '{
     "to_": "0x687422eea2cb73b5d3e242ba5456b782919afc85",
     "gasprice": 19000000000,
     "startgas":314150,
     "description": "from second address", 
     "type": "send", 
     "value": 60000000
  }'
  -H "Authorization: <jwt token>"
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "0x1cc19b3a7f80d12b992c5bed3f101548b374d2c9c4804fde4d02508c36e4fcbc"
    }
}
```


```shell
curl -X POST "https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions"
  -d '
"fee": "fastestFee",
"description": "First", 
"type": "send", 
"to_": [
        {
            "amount": "87269815", 
            "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
        },
        {
            "amount": "99988700", 
            "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
        },
    ]
}'
   -H "Authorization: <jwt token>"

```
> The above command returns JSON structured like this:
```json
{
    "data": {
        "hash": "402cc503487d6a26ffb4185ada70cce28d960060ec33dd519615df96eaabadea"
    }
}
```

