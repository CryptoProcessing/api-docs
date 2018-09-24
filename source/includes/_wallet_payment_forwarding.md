# Wallet's payment forwarding

Payment forwarding points to what address to transfer the arriving money.

## Payment forwarding object

> Example

```json
{
    "id": "a1c28479-6e6c-4504-87ed-ea56ab09cafc",
    "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
    "blocks_count": 1,
    "charge": 50000
}
```

Represents webhook object
 
### Attributes:

Attribute | Description
--------- | -----------
`id` | Payment forwarding ID
`address` | The address to which money will be transferred
`blocks_count` | The expected number of confirmations for the incoming transaction. Valid value from 0 to 100
`charge` | GasPrice (wei) for ETH and Fee (satoshi) for BTC


## Create payment forwarding

> POST https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token 7be2eda859eec7ebf8c21256bc55f498002e872e6f6ddfcff655e18bccf00000' \
  -H 'Content-Type: application/json' \
  -d '{
    "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
    "blocks_count": 1,
    "charge": 50000
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
        "blocks_count": 1,
        "charge": "50000.0"
    }
}
```

## Return payment forwarding

> GET https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token 7be2eda859eec7ebf8c21256bc55f498002e872e6f6ddfcff655e18bccf00000' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
        "blocks_count": 1,
        "charge": "50000.0"
    }
}
```


## Update payment forwarding

> PUT https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X PUT \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token 7be2eda859eec7ebf8c21256bc55f498002e872e6f6ddfcff655e18bccf00000' \
  -H 'Content-Type: application/json' \
  -d '{
    "address": "1N8hwYGo2uvFGr6z1Hysp3j7V9nBrZ1dmm",
    "blocks_count": 2,
    "charge": 500000
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1N8hwYGo2uvFGr6z1Hysp3j7V9nBrZ1dmm",
        "blocks_count": 2,
        "charge": "500000.0"
    }
}
```


## DELETE payment forwarding

> DELETE https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X DELETE \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token 7be2eda859eec7ebf8c21256bc55f498002e872e6f6ddfcff655e18bccf00000' \
  -H 'Content-Type: application/json'
```

> The above command returns only HTTP code (204) if payment forwarding removed and code (404) if payment forwarding for wallet doesn't exist
