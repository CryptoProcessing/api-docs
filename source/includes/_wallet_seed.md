# Wallet's seed

## Seed object

> Example

```json
{
    "seed": "task olympic spoon remove answer method divert wet stick stuff cause trick",
    "segwit_type": "non_native"
}
```

### Attributes:

Attribute      | Description
---------      | -----------
`seed`         | Seed recovery phrase
`segwit_type`  | Only for bitcoin (legacy, non-native, native). Not required.

## Get wallet's seed

> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/seed

> Example request

```shell
curl -X GET \
  https://cryptoprocessing.io/api/v1/wallets/45346ce2-b905-49f9-8463-cb0959c93784/seed \
  -H 'Authorization: Token <jwt token>' \
  -H 'Content-Type: application/json' 
```

> Example response

```json
{
    "data": {
        "seed": "task olympic spoon remove answer method divert wet stick stuff cause trick",
        "segwit_type": "non_native"
    }
}
```

## Create wallet by seed phrase

> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/seed

> Example request

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/seed \
  -H 'Authorization: Token <jwt token>' \
  -H 'Content-Type: application/json' \
  -H 'Idempotency-Key: <token>' \
  -d '{
	"seed": "task olympic spoon remove answer method divert wet stick stuff cause trick",
	"name": "Wallet name",
	"currency": "BTC",
	"segwit_type": "native",
	"human": "Human name",
	"description": "Some description"
}'
```

> Example response

```json
{
    "data": {
        "id": "8961afc0-e2da-4807-a517-e82909c135ee",
        "name": "Wallet name",
        "currency": "BTC",
        "human": "Human name",
        "description": "Some description",
        "system_fee_percent": "1.0",
        "merchant_fee_percent": "0.0",
        "created_at": "2018-08-29T10:51:39.283Z",
        "updated_at": "2018-08-29T10:51:39.881Z"
    }
}
```
