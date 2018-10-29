# Wallet's transactions

The diff in comparison with Wallet's address transactions is that you *need to specify the sender address(es)* (`from_` field in requests)


## Create transaction (ETH)

Parameter             | Description
----------------------| ---------
`from_ `              | Sender address 
`to_ `                | Recipient address 
`description`         | Transaction description
`gas_price`           | GasPrice in ether
`gas_limit`           | GasLimit
`amount   `           | Amount in ether

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/acded3fc-5144-4726-b45b-d83fa56136b0/transactions \
  -H 'Authorization: <jwt token>' \
  -H 'Content-Type: application/json' \
  -d '{
	"from_": "0x822c09d5f89261c02d4fc0bb65bb45c7ea234efe",
    "to_": "0x8abAb4093391340180CACe15404866499bb7D701",
    "description": "Transaction [CURL]",		
    "gas_price": "0.0000000045",
    "gas_limit": 21000,
    "amount": "0.0000000000356"
}'
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "0x7a3ba664212845234dba3cc6ed37d1279226255d6d7878e2544a1b19f02d7f21"
    }
}
```

## Create transaction (BTC)

Parameter             | Description
---------             | ---------
`from_ `              | Sender addresses
`to_`                 | Recipient addresses with amount
`description`         | Transaction description
`fee`                 | "fastestFee", "halfHourFee", "hourFee" or value in bitcoin

> POST https://cryptoprocessing.io/api/v1/wallets/:wallet_id/transactions

```shell
curl -X POST \
  https://cryptoprocessing.io/api/v1/wallets/45346ce2-b905-49f9-8463-cb0959c93784/transactions \
  -H 'Authorization: <jwt token>' \
  -H 'Content-Type: application/json' \
  -d '{
        "from_": ["2N8QznL4ifxkg5nUakQL4aAwNTCREWrDdgv", "2N14ygepzQ51ymqw4WnUnPcu4cQkJ29EVgj"],
        "to_": [
            {
                "amount": "0.0001",
                "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
            },
            {
                "amount": "0.000013",
                "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
            }
        ],
        "description": "Transaction [CURL]",
        "fee": "hourFee"
    }'
```
> The above command returns JSON structured like this:
```json
{
    "data": {
        "hash": "44ea4b8e6ba8d4408e5d4d0e101a7c0cb0ad4391350dd1d885b4621a32ff9d30"
    }
}
```
