# Wallet's payment forwarding

Payment forwarding points to what address to transfer the arriving money.

## Payment forwarding object

> Example

```json
{
    "id": "a1c28479-6e6c-4504-87ed-ea56ab09cafc",
    "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
    "blocks_count": 1,
    "fee": "0.0000001"
}
```

> Example

```json
{
    "address": "0xE0bB087dc0F751F2b87E1323f1700F514EB635f0",
    "blocks_count": 1,
    "gas_price": "0.0003"
}
```

Represents webhook object
 
### Attributes:

Attribute         | Description
------------------|---------------
`id`              | Payment forwarding ID
`address`         | The address to which money will be transferred
`blocks_count`    | The expected number of confirmations for the incoming transaction. Valid value from 0 to 100
`gas_price`       | GasPrice for ETH
`fee`             | Fee for BTC


## Create payment forwarding

> POST https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
    "blocks_count": 1,
    "fee": "0.000001"
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
        "blocks_count": 1,
        "fee": "0.000001"
    }
}
```

## Return payment forwarding

> GET https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1LpkYGhsQEeE11KmsxdTmC6kM1vo1mk7b8",
        "blocks_count": 1,
        "fee": "0.000001"
    }
}
```


## Update payment forwarding

> PUT https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X PUT \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -d '{
    "address": "1N8hwYGo2uvFGr6z1Hysp3j7V9nBrZ1dmm",
    "blocks_count": 2,
    "fee": 0.000002"
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "d220089b-8cef-4374-968b-f1746354e840",
        "address": "1N8hwYGo2uvFGr6z1Hysp3j7V9nBrZ1dmm",
        "blocks_count": 2,
        "charge": "0.000002"
    }
}
```


## DELETE payment forwarding

> DELETE https://cryptoprocessing.io/api/v1/wallets/:id/payment_forwarding

> Example request

```shell
curl -X DELETE \
  https://cryptoprocessing.io/api/v1/wallets/1cf72914-d5fc-425b-ad72-ca9320d4cbcf/payment_forwarding \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json'
```

> The above command returns only HTTP code (204) if payment forwarding removed and code (404) if payment forwarding for wallet doesn't exist
