# Rescan 

## Rescan

Method available only for ETH family wallets

> POST "https://cryptoprocessing.io/api/v1/wallets/:wallet_id/transactions/rescan"

```shell
curl -X POST "https://cryptoprocessing.io/api/v1/wallets/ebdb4cc4-0b5e-48c5-93c4-59335a991b8b/transactions/rescan" \
-H "Content-Type: application/json" \
-H "Authorization: f5994c61abf297b8cc820d90f3a41256f653dd5b149e56b22dee242d23bbd23c" \
-d '{ "address": "0x75113e05edd43f5badc3e71d8a4b1c5c9b372f99" }'
```

> Response:

```json
{"data":{"status":"ok"}}
```
