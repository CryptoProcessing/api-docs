# Exchange Callbacks

## Callback object

> Example

```json
{
    "orders": [
        {
            "id": "d136f2e0-c938-4596-b226-140d557d5eda",
            "wallet_id": "a0f1f57d-322e-4a90-9f60-ca17387fa2c5",
            "address": "39Sqhiw9KVWWLBkHKRkMohatFnUhy7esYm",
            "tx_id": "8b4f535d4bae8e6219ee2f9be279a0a2ac6256573fc38df6a49e9f2e868d308e",
            "amount": "1.000023",
            "currency": "BTC",
            "filled": [
                {
                    "amount": "7960.02",
                    "currency": "USD",
                }
            ]
        }
    ]
}
```

Callbacks is used to sent notifications once exchange order is executed.

### Attributes:

Attribute | Description
--------- | -----------
`id` | Unique order ID
`wallet_id` | Wallet ID
`address` | Address was used for deposit
`tx_id` | Transaction ID was used for deposit
`amount` | Sold amount
`currency` | Wallet currency
`filled` | Array of stock orders values
