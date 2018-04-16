# Wallets

## Wallet object

> Example

```json
{
    "currency": "BTC",
    "wallet": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
    "default": false,
    "created_at": "2018-04-10T14:48:00.000Z"
}
```

Represents wallet object
 
### Attributes:

Attribute | Description
--------- | -----------
`currency` | Wallet currency
`wallet` | Wallet hash id
`default` | Wallet is default for currency
`created_at` | Wallet creation date

## Create wallet

Creates wallet

## Update wallet

> POST http://example.com/api/wallets/[wallet_id]

Updates wallet

### Attributes

> Example request

```shell
curl "http://example.com/api/wallets/1BoatSLRHtKNngkdXEeobR76b53LETtpyT"
  -X PUT
  -d '{"default": true}'
  -H "Authorization: <jwt token>"
```

> The above command returns JSON structured like this:

```json
{
    "currency": "BTC",
    "wallet": "1BoatSLRHtKNngkdXEeobR76b53LETtpyT",
    "default": true,
    "created_at": "2018-04-10T14:48:00.000Z"
}
```

Attribute | Description
--------- | -----------
`default` | Set wallet default for currency 

