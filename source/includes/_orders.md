# Orders

## Order object

> Example

```json
{
    "id": "d5b1002e-06dc-4bc4-bd02-d52f2a8c0b9c",
    "created_at": "2018-08-17T13:09:09.822Z",
    "updated_at": "2018-08-17T17:04:55.626Z",
    "amount": 40.0,
    "currency": "EUR",
    "status": "SUCCESS",
    "customer": {
      "email": "customer@example.com"
    },
    "external_payout_address": "2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
    "external_payout_amount": "1.105",
    "external_payout_currency": "BTC",
    "secret_for_success_redirect": "some_secret_key1",
    "secret_for_fail_redirect": "some_secret_key2",
}
```

Represents order object
 
### Attributes:

Attribute | Description
--------- | -----------
`id` | Order UUID
`created_at` | Order creation date and time
`updated_at` | Order updated at date and time
`amount` | Order's amount value, big float (up to 18 decimals)
`currency` | Order's currency. Available options: ["BTC", "ETH", "EUR", "RUB", "USD"]
`status` | Order's status. Available options: ["NEW", "PROCESSING", "PENDING", "SUCCESS", "FAIL"]
`customer` | Customer's info. Available hash keys: ["email"]
`external_payout_address` | Payout address related to payout currency
`external_payout_amount` | Payout amount to external address
`external_payout_currency` | Payout currency (what merchant takes)
`gas_limit` | Gas limit for external ethereum transaction
`secret_for_success_redirect` | Some secret key which will be included in GET params for success redirect endpoint
`secret_for_fail_redirect` | Some secret key which will be included in GET params for fail redirect endpoint


## Create order

Creates order

### Parameters:

Parameter | Description
--------- | -----------
`amount` | Order's amount value, big float (up to 18 decimals) **(required)**
`currency` | Order's currency. Available options: ["BTC", "ETH", "EUR", "RUB", "USD"] **(required)**
`external_payout_currency` | Payout currency (what merchant takes)
`external_payout_address` | Payout address related to payout currency
`external_payout_amount` | Payout amount to external address
`gas_limit` | Gas limit for external ethereum transaction
`customer` | Customer's info. Available hash keys: ["email"]
`check_amount` | The need for an approximate check of the correspondence between the amount of the fiat and the amount in cryptocurrency

> POST https://cryptoprocessing.io/api/v1/orders

> Example request

```shell
curl "https://cryptoprocessing.io/api/v1/orders" \
  -H "Authorization: Token <token>" \
  -H "Content-Type: application/json" \
  -H 'Idempotency-Key: bc4541e5-29b1-484e-89ad-ee9e7deba1c9' \
  -X POST \
  -d '{ "amount":50,
        "currency":"EUR",
        "external_payout_currency":"BTC",
        "external_payout_address":"2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
        "customer": {
          "email": "customer@example.com"
        },
        "check_amount": true
      }'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3",
    "created_at": "2018-08-17T18:39:12.106Z",
    "updated_at": "2018-08-17T18:39:13.217Z",
    "amount": "50.0",
    "currency": "EUR",
    "status": "NEW",
    "customer": {
      "email": "customer@example.com"
    },
    "external_payout_address": "2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
    "external_payout_currency": "BTC",
    "secret_for_success_redirect": "e5f295460e5e7b9c57fb2413f0e67598",
    "secret_for_fail_redirect": "023a4207e7286c216396b8508ddfdd0b"
    "payment_url": "http://cryptoprocessing.io/orders/9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3/pay",
    "check_amount": true
  }
}
```


## Return order

Returns order

> GET https://cryptoprocessing.io/api/v1/orders/:order_id

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/orders/9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3 \
  -H 'Authorization: Token <token>' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache'
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3",
    "created_at": "2018-08-17T18:39:12.106Z",
    "updated_at": "2018-08-17T18:39:13.217Z",
    "amount": "50.0",
    "currency": "EUR",
    "status": "NEW",
    "customer": {
      "email": "customer@example.com"
    },
    "external_payout_address": "2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
    "external_payout_amount":null,
    "external_payout_currency": "BTC",
    "secret_for_success_redirect": "e5f295460e5e7b9c57fb2413f0e67598",
    "secret_for_fail_redirect": "023a4207e7286c216396b8508ddfdd0b"
    "payment_url": "http://cryptoprocessing.io/orders/9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3/pay"
  }
}
```

## Payment link

By default, the order is processed using "crypto_card", you can change this behavior by adding a parameter "via" to payment link.

Available options of "via" parameter: "indacoin", "fx", "crypto_card", "etelaranta"


## Test Cards

For test transactions at `https://testnet.cryptoprocessing.io` you may use:

Card Number | Description
--------- | -----------
`4000 0000 0000 0002` | will be CONFIRMED as 3DS transaction
`5555 5555 5555 4444` | will be DECLINED as 3DS transaction
`4000 0000 0000 0077` | will be CONFIRMED as non-3DS transaction
`5555 5555 5555 4477` | will be DECLINED as non-3DS transaction

Testnet crypto will be transferred to your Merchant Wallet.
