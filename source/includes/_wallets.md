# Wallets

## Wallet object

> Example

```json
{
    "id": "a0f1f57d-322e-4a90-9f60-ca17387fa2c5",
    "name": "main",
    "currency": "BTC",
    "human": "Main BTC Wallet",
    "description": "Default BTC wallet with multiple addresses",
    "system_fee_percent": "0.0",
    "merchant_fee_percent": "0.0",
    "balance": "1.948",
    "created_at": "2018-08-14T16:44:26.925Z",
    "updated_at": "2018-08-21T12:22:37.391Z"
}
```

Represents wallet object
 
### Attributes:

Attribute | Description
--------- | -----------
`id` | Wallet ID
`name` | Wallet name
`currency` | Wallet's currency. Available options: ["BTC", "ETH", "EUR", "RUB", "USD"]
`human` | Wallet full name
`description` | Wallet description
`system_fee_percent` | Processing fee percent 
`merchant_fee_percent` | Merchant fee percent 
`balance` | Wallet balance (by default this field is present only for requesting a specific wallet, you need to add an extra parameter when you request an array of wallets so that the balance is displayed)
`created_at` | Wallet creation date and time
`updated_at` | Wallet updated date and time


## Create wallet

> POST https://cryptoprocessing.io/api/v1/wallets

> Example request

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets \
  -H 'Authorization: Token 4d0834297304689f7b7983007775610bdb856c7e15790e7d5c7f857e627fe568' \
  -H 'Content-Type: application/json' \
  -H 'Idempotency-Key: 7952c055-b8a1-498e-b0ea-737985e954c0' \
  -d '{
	"name": "crypto_btc",
	"currency": "BTC",
	"human": "Crypto BTC",
	"description": "For inner use of the new crypto-exchange"
}'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "8961afc0-e2da-4807-a517-e82909c135ee",
        "name": "crypto_btc",
        "currency": "BTC",
        "human": "Crypto BTC",
        "description": "For inner use of the new crypto-exchange",
        "system_fee_percent": "1.0",
        "merchant_fee_percent": "0.0",
        "created_at": "2018-08-29T10:51:39.283Z",
        "updated_at": "2018-08-29T10:51:39.881Z"
    }
}
```

## Return wallet

> POST https://cryptoprocessing.io/api/v1/wallet/:id

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/wallets/f17dc388-c93d-4934-87ca-b830151cb837 \
  -H 'Authorization: Token 7be2eda859eec7ebf8c21256bc55f498002e872e6f6ddfcff655e18bccf00000' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "f17dc388-c93d-4934-87ca-b830151cb837",
        "name": "main",
        "currency": "ETH",
        "human": "Main ETH Wallet",
        "description": "Default ETH wallet with multiple addresses",
        "system_fee_percent": "1.0",
        "merchant_fee_percent": "0.0",
        "balance": "0.5459715561",
        "created_at": "2018-09-03T07:02:15.860Z",
        "updated_at": "2018-09-03T07:02:16.195Z"
    }
}
```

## Wallets without balances

> GET https://cryptoprocessing.io/api/v1/wallets?page=1&limit=20

> Example request

```shell
curl -X GET \
  'https://cryptoprocessing.io/api/v1/wallets?page=1&limit=20' \
  -H 'Authorization: Token 4d0834297304689f7b7983007775610bdb856c7e15790e7d5c7f857e627fe568' \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 5,
        "current_page": 1,
        "last_page": 1,
        "limit": 20,
        "out_of_range": false
    },
    "data": [
        {
            "id": "a0f1f57d-322e-4a90-9f60-ca17387fa2c5",
            "name": "main",
            "currency": "BTC",
            "human": "Main BTC Wallet",
            "description": "Default BTC wallet with multiple addresses",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "created_at": "2018-08-14T16:44:26.925Z",
            "updated_at": "2018-08-21T12:22:37.391Z"
        },
        {
            "id": "c6136ee4-eabd-4cbe-aed8-ecd0ffdbcc4e",
            "name": "main",
            "currency": "ETH",
            "human": "Main ETH Wallet",
            "description": "Default ETH wallet with multiple addresses",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "created_at": "2018-08-14T16:44:27.478Z",
            "updated_at": "2018-08-21T12:22:38.231Z"
        },
        {
            "id": "3a488bed-1f03-4f89-9c04-0713d240c45f",
            "name": "main",
            "currency": "EUR",
            "human": "Main EUR Wallet",
            "description": "Default EUR wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "created_at": "2018-08-14T16:44:27.946Z",
            "updated_at": "2018-08-21T15:42:08.601Z"
        },
        {
            "id": "5b191e4b-e1c2-4e9c-8d0b-4c4ab87a4129",
            "name": "main",
            "currency": "RUB",
            "human": "Main RUB Wallet",
            "description": "Default RUB wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "created_at": "2018-08-14T16:44:27.950Z",
            "updated_at": "2018-08-21T12:22:35.378Z"
        },
        {
            "id": "50540b3f-3ebe-4397-8d96-80f78ad08e2d",
            "name": "main",
            "currency": "USD",
            "human": "Main USD Wallet",
            "description": "Default USD wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "created_at": "2018-08-14T16:44:27.954Z",
            "updated_at": "2018-08-21T12:22:35.866Z"
        }
    ]
}
```

## Wallets with balances

This request takes longer to execute than the request without balances

> GET https://cryptoprocessing.io/api/v1/wallets?page=1&limit=20&extra[]=balance

> Example request

```shell
curl -X GET \
  'https://cryptoprocessing.io/api/v1/wallets?page=1&limit=20&extra[]=balance' \
  -H 'Authorization: Token 4d0834297304689f7b7983007775610bdb856c7e15790e7d5c7f857e627fe568' \
  -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
    "_metadata": {
        "total": 5,
        "current_page": 1,
        "last_page": 1,
        "limit": 20,
        "out_of_range": false
    },
    "data": [
        {
            "id": "a0f1f57d-322e-4a90-9f60-ca17387fa2c5",
            "name": "main",
            "currency": "BTC",
            "human": "Main BTC Wallet",
            "description": "Default BTC wallet with multiple addresses",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "balance": "0.0",
            "created_at": "2018-08-14T16:44:26.925Z",
            "updated_at": "2018-08-21T12:22:37.391Z"
        },
        {
            "id": "c6136ee4-eabd-4cbe-aed8-ecd0ffdbcc4e",
            "name": "main",
            "currency": "ETH",
            "human": "Main ETH Wallet",
            "description": "Default ETH wallet with multiple addresses",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "balance": "0.0",
            "created_at": "2018-08-14T16:44:27.478Z",
            "updated_at": "2018-08-21T12:22:38.231Z"
        },
        {
            "id": "3a488bed-1f03-4f89-9c04-0713d240c45f",
            "name": "main",
            "currency": "EUR",
            "human": "Main EUR Wallet",
            "description": "Default EUR wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "balance": "0.0",
            "created_at": "2018-08-14T16:44:27.946Z",
            "updated_at": "2018-08-21T15:42:08.601Z"
        },
        {
            "id": "5b191e4b-e1c2-4e9c-8d0b-4c4ab87a4129",
            "name": "main",
            "currency": "RUB",
            "human": "Main RUB Wallet",
            "description": "Default RUB wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "balance": "0.0",
            "created_at": "2018-08-14T16:44:27.950Z",
            "updated_at": "2018-08-21T12:22:35.378Z"
        },
        {
            "id": "50540b3f-3ebe-4397-8d96-80f78ad08e2d",
            "name": "main",
            "currency": "USD",
            "human": "Main USD Wallet",
            "description": "Default USD wallet",
            "system_fee_percent": "0.0",
            "merchant_fee_percent": "0.0",
            "balance": "0.0",
            "created_at": "2018-08-14T16:44:27.954Z",
            "updated_at": "2018-08-21T12:22:35.866Z"
        }
    ]
}
```
