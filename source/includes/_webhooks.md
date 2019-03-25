# Webhooks

## Webhook object

> Example

```json
{
    "url": "https://example.com/webhook",
    "method": "POST",
    "events": ["transaction", "transaction_stale"],
    "active": true,
    "created_at": "2018-04-10T14:48:00.000Z"
}
```

Webhooks is used to sent event notifications.
 
### Attributes:

Attribute | Description
--------- | -----------
`url` | URL to call
`method` | HTTP Method to send callback, available only methods with body e.g. POST, PUT, PATCH
`events` | Array of binded events, '*' for any
`active` | Is current webhook active or not
`created_at` | Webhook creation date

## Get list

> GET http://example.com/api/webhooks

Returns list of webhooks

> Example request

```shell
curl "http://example.com/api/webhooks"
  -H "Authorization: Token <token>"
```

> Example response

```json
{
    webhooks: [
        {
            "url": "https://example.com/webhook",
            "method": "POST",
            "events": ["transaction", "transaction_stale"],
            "active": true,
            "created_at": "2018-04-10T14:48:00.000Z"
        }
    ]
}
```

## Create new

Creates new webhook

## Update webhook

Updates webhook

## Delete webhook

Deletes webhook
