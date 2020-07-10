# Wallet's address transactions 


## The ETH or TOKEN transaction object


Parameter             | Description
---------             | ---------
`hash`                | Transaction hash
`block_number`        | Block number where the transaction is included
`confirmations_count` | Transaction confirmation count
`description`         | Transaction description
`gas_price`           | Gas price
`gas_limit`           | Gas limit
`nonce`               | Ethereum transaction nonce
`type`                | Transaction type
`value`               | Transaction amount
`sender_address`      | A ethereum address of the sender
`receiver_address`    | A ethereum address of the recipient
`statuses`            | Array of transaction statuses
`forwarded_for`       | Hash of the transaction for which the forwarding was made


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
`forwarded_for`       | Hash of the transaction for which the forwarding was made

All possible transaction statuses:

- "non confirmed" - newly created transaction in the application, not sent to mempool  
- "queued" - transaction is in the queue to be sent  
- "in mempool" - transaction in mempool  
- "in block" - transaction is mined  
- "failed" - transaction is rejected  

Possible statuses for outgoing transactions:  
"non confirmed", "queued", "in mempool", "in block", "failed"

Possible statuses for incoming transactions:  
"in mempool", "in block", "failed"

## Get All transactions

Parameter             | Description
---------             | ---------
`wallet_id`           | Wallet ID
`address   `          | Address
`from_date`           | From date
`to_date`             | Before date
`page`                | Pagination starts at page 1, not at page 0 (page 0 will return the same results as page 1)
`limit`               | A limit on the number if objects to be returned. (default 25, max 100)
`from_address`        | Sender address
`to_address`          | Receiver address
`order_by`            | Available values: "date"
`sort`                | Available values: "asc" (default), "desc"


> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions

```shell
curl "https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/transactions?
&from_date=2016-04-12T00:00:00.000Z&to_date=2019-04-30T00:00:00.01100Z&page=1&limit=10&order_by=date&sort=desc
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
            "hash": "0xa59ae3c19ab383143918cfe032271e2182855a5a3449f068f533379e4ea46fab",
            "block_number": 4267539,
            "confirmations_count": 302,
            "description": "Incoming transaction",
            "gas_price": "0.000000111",
            "gas_limit": 21000,
            "nonce": 94,
            "type": "receive",
            "value": "2.0",
            "sender_address": "0x8abAb4093391340180CACe15404866499bb7D701",
            "receiver_address": "0x05cb0eab06fbb7ab1aa5708bab3bce35b6bff336",
            "forwarded_for": "0x11a37d55786b781b01dda4405646c43bcc36574b45b9f83470ebd19fba7470c3",
            "statuses": [
                {
                    "status": "in mempool",
                    "date": "Fri, 19 Oct 2018 10:06:58 GMT"
                },
                {
                    "status": "in block",
                    "date": "Fri, 19 Oct 2018 10:07:06 GMT"
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
            "hash": "ea574e5982434a920b6d3be80090fb8da97f6f4d20c7eb522c9c36772a81fad9",
            "amount": "0.00013",
            "block_number": 1439531,
            "confirmations_count": 11,
            "fee": "0.00001",
            "type": "send",
            "description": "Transaction [CURL]",
            "forwarded_for": "3b10b68f8703efae9c71134feeca6770670e1e2aae78faba9868da0d341fa157",
            "receiver_addresses": [
                {
                    "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB",
                    "amount": "0.0001"
                },
                {
                    "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB",
                    "amount": "0.00003"
                },
                {
                    "address": "2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv",
                    "amount": "0.01453181"
                }
            ],
            "sender_addresses": [
                {
                    "address": "2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv"
                }
            ],
            "statuses": [
                {
                    "status": "non confirmed",
                    "date": "Fri, 19 Oct 2018 10:11:24 GMT"
                },
                {
                    "status": "in mempool",
                    "date": "Fri, 19 Oct 2018 10:11:24 GMT"
                },
                {
                    "status": "in block",
                    "date": "Fri, 19 Oct 2018 10:36:37 GMT"
                }
            ]
        }
    ]
}
```


## Create BTC transaction

Parameter             | Description
---------             | ---------
`to_`                 | Recipient addresses with amount
`description`         | Transaction description
`fee`                 | "fastestFee", "halfHourFee", "hourFee" or value in bitcoin

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/45346ce2-b905-49f9-8463-cb0959c93784/addresses/2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv/transactions \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "to_": [
        {
            "amount": "0.0001",
            "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
        },
        {
            "amount": "0.00003",
            "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
        }
    ],
    "description": "Transaction [CURL]",
    "fee": "hourFee"
}'
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "2d4217e45c1e3ff6a1257a95662eebce30bb6ac195e874fb3fbcd337dff5f464"
    }
}
```

## Create ETH transaction

Parameter             | Description
----------------------| ---------
`to_ `                | Recipient address 
`description`         | Transaction description
`gas_price`           | GasPrice in ether
`gas_limit`           | GasLimit
`amount`              | Amount in ether

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/568c5ed2-10c5-4a80-b91d-5a80f8e1f7e0/addresses/0x05cb0eab06fbb7ab1aa5708bab3bce35b6bff336/transactions \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "to_": "0x8abAb4093391340180CACe15404866499bb7D701",
    "description": "Transaction [CURL]",		
    "gas_price": "0.00000000001",
    "gas_limit": 21000,
    "amount": "0.0000000505"
}'
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "0x1cc19b3a7f80d12b992c5bed3f101548b374d2c9c4804fde4d02508c36e4fcbc"
    }
}
```

## Create TOKEN transaction

Parameter                       | Description
--------------------------------| ---------
`to_ `                          | Recipient address
`description`                   | Transaction description
`gas_price`                     | GasPrice in ether
`gas_limit`                     | GasLimit
`amount`                        | Amount in tokens
`use_liquidity_wallet_for_fee`  | Payment of commission with liquidity wallet (true/false)

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/ae8e53dd-c42e-43b1-9b6f-eecb2c4aa934/addresses/0xf019ea768e154219935ff957f2216c66d9eb802a/transactions \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "to_": "0x8abAb4093391340180CACe15404866499bb7D701",
    "description": "Transaction [CURL]",
    "gas_price": "0.0000000001",
    "gas_limit": 150000,
    "amount": "100.005",
    "use_liquidity_wallet_for_fee": false
}'
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "0x1cc19b3a7f80d12b992c5bed3f101548b374d2c9c4804fde4d02508c36e4fcbc"
    }
}
```

## Create USDT transaction

Parameter             | Description
---------             | ---------
`to_`                 | Recipient addresses
`amount`              | Amount
`description`         | Transaction description

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/73b819fb-0332-24ec-8ac9-49a247c3299a/addresses/2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv/transactions \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "to_": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB",
    "amount": "0.01",
    "description": "Transaction [CURL]"
}'
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "2d4217e45c1e3ff6a1257a95662eebce30bb6ac195e874fb3fbcd337dff5f464"
    }
}
```
