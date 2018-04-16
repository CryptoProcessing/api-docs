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
    "name": "New wallet",
    "type": "Multisig wallet"
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


## Update an account

Updates an account
