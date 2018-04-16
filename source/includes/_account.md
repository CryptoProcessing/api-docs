# Account

This is an object representing your account. 

## The account object

> Example response

```json
{
    "email": "mail@example.com",
    "id": "c582e3f2-1ded-4696-8b7f-28516f546d0f",
    "currency": "BTC",
    "created_at": "2018-04-16T15:30:00.000Z",
    "name": "New account",
    "type": "Multisig account"
}
```
 
### Attributes:

Attribute | Description
--------- | -----------
`email` | Account email
`id`| Account id 
`currency` | Account currency
`created_at` | Account creation date
`name`| Account description
`type`| Account type



## Create an account

> POST http://example.com/api/account


Creates an account for further work with processing.

> Example request

```shell
curl "http://example.com/api/account"
  -X POST
  -d '{"email": "mail@example.com",
        "name": "New account",
         "type": "multisig",
         "currency": "BTC"}'
  -H "Authorization: <jwt token>"
```


> Example response

```json
{
    account: [
        {
            "email": "mail@example.com",
            "id": "c582e3f2-1ded-4696-8b7f-28516f546d0f",
            "currency": "BTC",
            "created_at": "2018-04-16T15:30:00.000Z",
            "name": "New account",
            "type": "Multisig account"
        }
    ]
}
```


## Update an account

Updates an account
