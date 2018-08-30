# Wallet's address transactions 


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

> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions

```shell
curl "https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions"
  -H "Authorization: Token <token>"
```

> For the Ethereum the above command returns JSON structured like this:

```json
{
    "data": {
        "transactions": [
            {
                "block_number": 3044794,
                "confirmations_count": 5353,
                "data": "0x",
                "description": "Incoming transaction",
                "fromaddress": "0x687422eEA2cB73B5d3e242bA5456b782919AFc85",
                "gasprice": 18000000000,
                "startgas": 314150, 
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
                "startgas": 314150, 
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
}
```
> For the Bitcoin the above command returns JSON structured like this:

```json
{
    "data": {
        "transactions": [
            {
                "amount": 87269815,
                "block_number": 1287048,
                "confirmations_count": 2725,
                "created_at": "Thu, 01 Mar 2018 14:42:41 GMT",
                "currency": "btc",
                "description": "First",
                "id": "7a23f17f7e01384599732bba37b6fb175a27cddddbba9a0bdffa56febc22672f",
                "receiver_addresses": [
                    {
                        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB",
                        "amount": 87269815
                    },
                    {
                        "address": "mvZK9A1JXE87puEbudsqPNxiye1StLZ7se",
                        "amount": 99988700
                    }
                ],
                "sender_addresses": [
                    {
                        "address": "mvZK9A1JXE87puEbudsqPNxiye1StLZ7se"
                    }
                ],
                "statuses": [
                    {
                        "date": "Thu, 01 Mar 2018 14:42:41 GMT",
                        "status": "non confirmed"
                    },
                    {
                        "date": "Thu, 01 Mar 2018 14:42:42 GMT",
                        "status": "in mempool"
                    },
                    {
                        "date": "Thu, 01 Mar 2018 14:50:28 GMT",
                        "status": "in block"
                    }
                ],
                "type": "send"
            }
        ]
    }
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

