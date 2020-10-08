# Address validation

## Validate address 

To validate an address in **mainnet**, you need to make a request to **cryptoprocessing.io** domain. 
If you want to validate addresses in **testnet**, you need to make a request to **testnet.cryptoprocessing.io** domain.

URL structure: /api/v1/validate/*:currency*/*:address*

Attribute  | Description
---------  | -----------
`currency` | currency, available currencies: eth, btc 
`address`  | address for specified currency 

> https://cryptoprocessing.io/api/v1/validate/btc/2NGZrVvZG92qGYqzTLjCAewvPZ7JE8S8VxE

```json
{
    "data": {
        "is_valid": false
    }
}
```

> https://testnet.cryptoprocessing.io/api/v1/validate/btc/2NGZrVvZG92qGYqzTLjCAewvPZ7JE8S8VxE

```json
{
    "data": {
        "is_valid": true
    }
}
```

> https://cryptoprocessing.io/api/v1/validate/eth/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2

```json
{
    "data": {
        "is_valid": true
    }
}
```
