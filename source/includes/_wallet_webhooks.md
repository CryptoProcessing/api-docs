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
