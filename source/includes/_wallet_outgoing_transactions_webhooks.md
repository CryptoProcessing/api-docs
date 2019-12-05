# Wallet's Webhooks for Outgoing Transactions

## Webhook Payload

> Example for a new operation

```json
{
  "approved": false,
  "approved_at": null,
  "created_at": "2019-12-05T22:31:19.854Z",
  "data": {
    "type": "send",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "from_": [
      "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx"
    ],
    "fee": "hourFee"
  },
  "declared_params": {
    "id": "6d121844-31d4-4de8-8320-5dd17f36193e",
    "from_": "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "fee": "hourFee"
  },
  "declined": false,
  "declined_at": null,
  "error": null,
  "has_error": null,
  "id": "3cafa58f-9725-4eca-93ff-59ad07767bb6",
  "lock_version": 0,
  "result": null,
  "txid": null,
  "updated_at": "2019-12-05T22:31:19.854Z",
  "wallet_id": "6d121844-31d4-4de8-8320-5dd17f36193e"
}
```

> Example for a declined operation

```json
{
  "approved": false,
  "approved_at": null,
  "created_at": "2019-12-05T22:31:19.854Z",
  "data": {
    "type": "send",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "from_": [
      "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx"
    ],
    "fee": "hourFee"
  },
  "declared_params": {
    "id": "6d121844-31d4-4de8-8320-5dd17f36193e",
    "from_": "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "fee": "hourFee"
  },
  "declined": true,
  "declined_at": "2019-12-05T22:52:45.948Z",
  "error": null,
  "has_error": null,
  "id": "3cafa58f-9725-4eca-93ff-59ad07767bb6",
  "result": null,
  "txid": null,
  "updated_at": "2019-12-05T22:52:45.960Z",
  "wallet_id": "6d121844-31d4-4de8-8320-5dd17f36193e"
}
```

> Example for approved operation

```json
{
  "approved": true,
  "approved_at": "2019-12-05T22:54:57.667Z",
  "created_at": "2019-12-05T22:52:35.984Z",
  "data": {
    "type": "send",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "from_": [
      "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx"
    ],
    "fee": "hourFee"
  },
  "declared_params": {
    "id": "6d121844-31d4-4de8-8320-5dd17f36193e",
    "from_": "2MxDEYUuFaVHY5gRsLhodscU3rQ3gcxxNXx",
    "to_": [
      {
        "amount": 50000,
        "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
      }
    ],
    "fee": "hourFee"
  },
  "declined": false,
  "declined_at": null,
  "error": null,
  "has_error": false,
  "id": "784b1d57-0364-449c-a71c-967143ea01a0",
  "result": {
    "status": "success",
    "transaction": "4ba3d9942f6f882ab356707beb5ee54c3e4a79a933cb3aca004bdf13e5fd37c8"
  },
  "txid": "4ba3d9942f6f882ab356707beb5ee54c3e4a79a933cb3aca004bdf13e5fd37c8",
  "updated_at": "2019-12-05T22:55:00.494Z",
  "wallet_id": "6d121844-31d4-4de8-8320-5dd17f36193e"
}
```
