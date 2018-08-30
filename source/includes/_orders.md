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
    "secret_for_success_redirect": "some_secret_key1",
    "secret_for_fail_redirect": "some_secret_key2",
    "external_payout_address": "2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
    "external_payout_currency": "BTC"
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
`external_payout_address` | Payout address related to pyout currency
`external_payout_currency` | Payout currency (what merchant takes)
`secret_for_success_redirect` | Some secret key which will be included in GET params for success redirect endpoint
`secret_for_fail_redirect` | Some secret key which will be included in GET params for fail redirect endpoint


## Create order

Creates order

> POST https://cryptoprocessing.io/api/v1/orders

> Example request

```shell
curl "https://cryptoprocessing.io/api/v1/orders" \
  -H "Authorization: Token 4d0834297304689f7b7983007775610bdb856c7e15790e7d5c7f857e627fe568" \
  -H "Content-Type: application/json" \
  -H 'Idempotency-Key: bc4541e5-29b1-484e-89ad-ee9e7deba1c9' \
  -X POST \
  -d '{ "amount":50, "currency":"EUR", "external_payout_currency":"BTC", "external_payout_address":"2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M" }'
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
    "external_payout_address": "2N5kUa6RqcDx8NZsuLQFkifumUz9gCWC54M",
    "external_payout_currency": "BTC",
    "secret_for_success_redirect": "e5f295460e5e7b9c57fb2413f0e67598",
    "secret_for_fail_redirect": "023a4207e7286c216396b8508ddfdd0b"
    "payment_url": "http://cryptoprocessing.io/orders/9bf8fec7-bc12-446f-a1a4-7ec4d5caa3d3/pay"
  }
}
```

