# Invoice processing

## Invoice object

> Example

```json
{
    "id": "3cc95f4b-8b14-4c02-95e2-0002b77caa4d",
    "store_id": "8f314370-83ab-4c00-8c77-c9874d4b2a6a",
    "amount": "1001.54",
    "currency": "EUR",
    "status": "NEW",
    "success_redirect_url": "https://example.com/process/success",
    "error_redirect_url": "https://example.com/process/error",
    "created_at": "2020-12-28T10:10:34.791Z",
    "updated_at": "2020-12-28T10:10:34.791Z",
    "customer_email": "customer@example.com",
    "btc_address": "2N84FHPk745t1Ws7vjTX2V4UTvDtwMVfzQq",
    "btc_amount": "0.045762499579444076",
    "btc_rate": "0.000045692133693556",
    "usd_amount": "1181.8172",
    "usd_rate": "1.18"
}
```

### Attributes: 

Attribute                   | Description
--------------------------- | -----------
`id`                        | Invoice ID 
`store_id`                  | Store ID
`amount`                    | Amount set at invoice creation
`currency`                  | Settlement currency, available values: "EUR"
`status`                    | Available statuses: "NEW", "PAID"
`success_redirect_url`      | Redirect url for paid invoice
`error_redirect_url`        | URL for "RETURN TO STORE" link   
`created_at`                | Time of creation
`updated_at`                | Time of updating 
`customer_email`            | Customer email 
`btc_address`               | BTC address 
`btc_amount`                | BTC amount 
`btc_rate`                  | BTC per settlement currency  
`usd_amount`                | USD amount 
`usd_rate`                  | USD per settlement currency  


## Create invoice 

> POST https://cryptoprocessing.io/api/v1/checkout/stores/:store_id/invoices

> Example request

```shell
curl --location --request POST 'https://cryptoprocessing.io/api/v1/checkout/stores/8f314370-83ab-4c00-8c77-c9874d4b2a6a/invoices' \
--header 'Content-Type: application/json' \
--header 'Authorization: Token <token>' \
--data-raw '{
    "amount": "1001.54",
    "currency": "EUR",
    "customer_email": "customer@example.com",
    "success_redirect_url": "https://example.com/process/success",
    "error_redirect_url": "https://example.com/process/error"
}'
```

> The above command returns JSON structured like this:

```json
{
    "id": "165152de-4fde-4c40-ab3e-354a580c8e99",
    "store_id": "8f314370-83ab-4c00-8c77-c9874d4b2a6a",
    "amount": "1001.54",
    "currency": "EUR",
    "status": "NEW",
    "success_redirect_url": "https://example.com/process/success",
    "error_redirect_url": "https://example.com/process/error",
    "created_at": "2020-12-30T12:49:49.899Z",
    "updated_at": "2020-12-30T12:49:49.899Z",
    "customer_email": "customer@example.com",
    "btc_address": "2N9HjtJZLvoiZ4kpXnJv9nGPSAYydEQhJQW",
    "btc_amount": "0.044237474907194096",
    "btc_rate": "0.000044169453948114",
    "usd_amount": "1181.8172",
    "usd_rate": "1.18"
}
```

## Show invoice 

> GET https://cryptoprocessing.io/api/v1/checkout/stores/:store_id/invoices/:invoice_id

> Example request

```shell
curl --location --request GET 'http://cryptoprocessing.io/api/v1/checkout/stores/8f314370-83ab-4c00-8c77-c9874d4b2a6a/invoices/7e0eea17-5433-4879-b0e0-52081fbf7431' \
--header 'Content-Type: application/json' \
--header 'Authorization: Token <token>'
```

> The above command returns JSON structured like this:

```json
{
    "id": "165152de-4fde-4c40-ab3e-354a580c8e99",
    "store_id": "8f314370-83ab-4c00-8c77-c9874d4b2a6a",
    "amount": "1001.54",
    "currency": "EUR",
    "status": "NEW",
    "success_redirect_url": "https://example.com/process/success",
    "error_redirect_url": "https://example.com/process/error",
    "created_at": "2020-12-30T12:49:49.899Z",
    "updated_at": "2020-12-30T12:49:49.899Z",
    "customer_email": "customer@example.com",
    "btc_address": "2N9HjtJZLvoiZ4kpXnJv9nGPSAYydEQhJQW",
    "btc_amount": "0.044237474907194096",
    "btc_rate": "0.000044169453948114",
    "usd_amount": "1181.8172",
    "usd_rate": "1.18"
}
```

## Invoice webhook

### Callback object

> Example

```json
{
    "id": "165152de-4fde-4c40-ab3e-354a580c8e99",
    "store_id": "8f314370-83ab-4c00-8c77-c9874d4b2a6a",
    "amount": "1001.54",
    "currency": "EUR",
    "status": "PAID",
    "success_redirect_url": "https://example.com/process/success",
    "error_redirect_url": "https://example.com/process/error",
    "created_at": "2020-12-30T12:49:49.899Z",
    "updated_at": "2020-12-30T12:49:49.899Z",
    "customer_email": "customer@example.com",
    "btc_address": "2N9HjtJZLvoiZ4kpXnJv9nGPSAYydEQhJQW",
    "btc_amount": "0.044237474907194096",
    "btc_rate": "0.000044169453948114",
    "usd_amount": "1181.8172",
    "usd_rate": "1.18"
}
```

Callbacks is used to sent notifications once invoice is updated. 
