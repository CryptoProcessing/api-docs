# Wallet's transactions

The diff in comparison with Wallet's transactions is that you *need to specify the sender address(es)* (`from` field in requests)


## The transaction object


Parameter             | Description
---------             | ---------
`id`                  | Transaction id
`tx_hash`             | Transaction hash
`fromaddress`         | A ethereum address of the sender
`toaddress`           | A ethereum address of the recipient
`gasprice`            | Gas price
`block_number`        | Block number where the transaction is included
`confirmations_count` | Transaction confirmation count
`description`         | Transaction description
`data`                | Ethereum transaction data 
`nonce`               | Ethereum transaction nonce
`type`                | Transaction type
`value`               | Transaction amount 
`statuses`            | Array of transaction statuses


## Create A Transaction

> POST https://cryptoprocessing.io/api/v1/wallets/:id/transactions

```shell
curl -X POST "https://cryptoprocessing.io/api/v1/wallets/:id/transactions"
 -d '{
        "from_": "0xe17F97b518E9E8bBC9b72Ab88fd3f9db10BeA981",
        "to_": "0x687422eea2cb73b5d3e242ba5456b782919afc85",
        "gasprice": 19000000000,
        "startgas":314150,
        "description": "from second address", 
        "type": "send", 
        "value": 60000000
  }'
  -H "Authorization: <jwt token>"
```
> The above command returns JSON structured like this:

```json
{
    "data": {
        "hash": "0x1cc19b3a7f80d12b992c5bed3f101548b374d2c9c4804fde4d02508c36e4fcbc"
    }
}
```


```shell
curl -X POST "https://cryptoprocessing.io/api/v1/wallets/:id/transactions"
  -d '{"from_":
	[
		"mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
	],
"fee": "fastestFee",
"description": "First", 
"type": "send", 
"to_": [
		{
			"amount": "87269815", 
			"address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
		},
    {
      "amount": "99988700", 
      "address": "mv4rnyY3Su5gjcDNzbMLKBQkBicCtHUtFB"
    },
	]
}'
   -H "Authorization: <jwt token>"

```
> The above command returns JSON structured like this:
```json
{
    "data": {
        "hash": "402cc503487d6a26ffb4185ada70cce28d960060ec33dd519615df96eaabadea"
    }
}
```

