# Rescan transfers 

## Rescan transfers

Method available only for ETH family wallets

> GET https://cryptoprocessing.io/api/v1/wallets/:wallet_id/addresses/:address_id/rescan_transfers

```shell
curl "https://cryptoprocessing.io/api/v1/wallets/ebdb4cc4-0b5e-48c5-93c4-59335a991b8b/addresses/0x75113e05edd43f5badc3e71d8a4b1c5c9b372f99/rescan_transfers \
-H "Content-Type: application/json" \
-H "Authorization: XXX"
```

> Response:

```json
{"data":{"status":"ok"}}
```
