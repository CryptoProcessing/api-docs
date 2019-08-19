# Wallet's webhooks

With the help of webhooks you will receive notifications about transactions in the blockchain. Maximum number of webhooks 20.

## Webhook object

> Example

```json
{
    "id": "746d6b9e-7ce2-4231-87ea-d746a6f40db2",
    "url": "https://emample.com/endpoint",
    "max_confirmations": 6,
    "max_retries": 3
}
```

Represents webhook object
 
### Attributes:

Attribute | Description
--------- | -----------
`id` | Webhook ID
`url` | Webhook url
`max_confirmations` | The number of transaction confirmations in the blockchain to be notified about. Valid value from 0 to 100
`max_retries` | Maximum number of attempts to send a webhook. Valid value from 0 to 100


## Create webhook

> POST https://cryptoprocessing.io/api/v1/wallets/:id/webhooks

> Example request

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/webhooks \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "url": "https://emample.com/endpoint",
    "max_confirmations": 6,
    "max_retries": 3
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "485380ca-5b59-4236-976c-20429c68e3ff",
        "url": "https://emample.com/endpoint",
        "max_confirmations": 6,
        "max_retries": 3
    }
}
```

## Return webhooks

> GET https://cryptoprocessing.io/api/v1/wallets/:id/webhooks

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/webhooks \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 2
    },
    "data": [
        {
            "id": "f6303175-c86e-4ff4-81b8-40f23e6b3402",
            "url": "https://emample.com/endpoint1",
            "max_confirmations": 2,
            "max_retries": 1
        },
        {
            "id": "485380ca-5b59-4236-976c-20429c68e3ff",
            "url": "https://emample.com/endpoint2",
            "max_confirmations": 6,
            "max_retries": 3
        }
    ]
}
```


## Delete webhook

> DELETE https://cryptoprocessing.io/api/v1/wallets/:id/webhooks/:webhook_id

> Example request

```shell
curl -X DELETE \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/webhooks/cd0d8b1d-b20a-41f0-80d1-faf2c4629a82 \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json'
```

> The above command returns only HTTP code (204)


## Webhook request

Represents the request body from our server.

Possible attribute values.

**event.event_type:**  
UPDATE  
CREATE  
DELETE  
PENDING  
QUEUED  
FAILED  
SUCCESS  

**transaction.type:**  
receive  
send  
sendraw  
send_token  

> Webhook for ETH

```json
{
  "account": {
    "id": "1f02413b-c08e-1eef-b3b7-f6b07c136d01"
  },
  "transaction": {
    "hash": "0x976d866a7e5cb9f0106fd74f48b4ebf9f484067cf786a541b012099e28fbd2a6",
    "position": null,
    "from_address": "0x235cE7409D8Dfc72D0B6377761dc9c20e3967198",
    "to_address": "0x8cbbbf681ee97e4bf86fa54ae171d7efa108d867",
    "value": 2133990000000000,
    "gas_price": 7000000000,
    "nonce": 0,
    "input_data": "0x",
    "type": "receive"
  },
  "event": {
    "event_type": "SUCCESS",
    "event_group": "TX"
  },
  "block_number": 5981239,
  "confirmation": 0
}
```

> Webhook for TOKEN

```json
{
  "account": {
    "id": "d18108eb-bee5-4b41-be5b-e6156a496147"
  },
  "transaction": {
    "hash": "0x8abb8862899c19c04b7ce517d54cd6a5aabd5858683be854a2f634e3dd9990a0",
    "position": 0,
    "from_address": "0x274F3c32C90517975e29Dfc209a23f315c1e5Fc7",
    "to_address": "0xefbd0c505ad422134e6cd1a8af63b9c70ed538e9",
    "value": 1.0085e+21,
    "gas_price": 50000000000,
    "nonce": 134458,
    "input_data": "0xa9059cbb000000000000000000000000efbd0c505ad422134e6cd1a8af63b9c70ed538e9000000000000000000000000000000000000000000000036abbfbebced720000",
    "type": "receive",
    "currency": "ABX"
  },
  "event": {
    "event_type": "UPDATE",
    "event_group": "TX"
  },
  "block_number": 6937111,
  "confirmation": 3
}
```

> Webhook for BTC

```json
{
  "event": {
    "event_type": "CREATE",
    "event_group": "TX"
  },
  "block_number": null,
  "account": {
    "id": "1af71414-bdf1-4a16-9b41-133f5b6b9ae1"
  },
  "confirmation": 0,
  "transaction": {
    "ins": [
      {
        "script": "47304402207a8e712b394f5abb98f2f3c710babe8dbc7b2da7e57aa3dfcbbed08807b90c2c022055cd332d047cce7eeff4bd8b319b90a5899811d22f8e7f8fa32fda07a91e95d80121035a9347865719fe1f7aae59dcb19f6eb70a471808d5424a41013177dbab92b26a",
        "address": "13jrfpw3tRppxNrfaBxmWtrKnAG6EEteUa",
        "position": 0,
        "previous_hash": "c917b524fc65a378e872bcc65c86c751246d5be7d4708f4e299a0026cfc89645"
      },
      {
        "script": "473044022002724d5e5216296bd34e94afc617bbd12258efd2efac2e94da6655c843f4d8e4022047ada12af99bb0fa31a6f2dc7022fb804aa52dbd96e6e63e4fa3b29dbcbf5e780121036a06338df7b1af63e76e7f46af27874762ca5d87cd9be8cb21043a57d7a42b08",
        "address": "14sQ2ERZaeEUHXZ94ZAbjuKbPaeSuisDYp",
        "position": 0,
        "previous_hash": "131091397a2c3ae643af545d8aa5f9f2409b78aef3914bb9f9100d288b11205e"
      }
    ],
    "outs": [
      {
        "position": 0,
        "address": "32ZVTU6oHMBqMemArPaQuXtV2zroMqZ2to",
        "script": "a914098bc818d1e632a9bf9023d49ff5f50ad19d54d987",
        "value": 808035
      },
      {
        "position": 1,
        "address": "18SJDwJKYpnKppedyBZpURgFrjHqveEGf1",
        "script": "76a9145191a816dec73e10c4de7dbaebba8d8785be1d7d88ac",
        "value": 2028090
      }
    ],
    "hash": "964755b5fdff53807a9df96a33bfd5b7af832beb827d5117f181a08ede0fba7c",
    "lock_time": 538363,
    "position": null
  }
}
```
