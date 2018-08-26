# Introduction

## Idempotent Requests

```shell
curl "https://cryptoprocessing.io/api/v1/ping" \
  -H "Authorization: Token fe7409b0c9b3fc37ec6dfa027e7e9ca943e37ed9d31b3d98d5c06bdec1b76c7d" \
  -H "Idempotency-Key: 60Nk1zqhQJDoFnKj"
```

The API supports idempotency for safely retrying requests without accidentally performing the same operation twice. For example, if a request to create a charge fails due to a network connection error, you can retry the request with the same idempotency key to guarantee that only a single charge is created.

`GET` and `DELETE` requests are idempotent by definition, meaning that the same backend work will occur no matter how many times the same request is issued. You shouldn't send an idempotency key with these verbs because it will have no effect.

To perform an idempotent request, provide an additional Idempotency-Key: <key> header to the request.

How you create unique keys is up to you, but we suggest using V4 UUIDs or another appropriately random string. We'll always send back the same response for requests made with the same key, and keys can't be reused with different request parameters. Keys expire after 24 hours.

## Request IDs

Each API request has an associated request identifier. You can find this value in the response headers, under `Request-Id`. You can also find request identifiers in the URLs of individual request logs in your Dashboard. If you need to contact us about a specific request, providing the request identifier will ensure the fastest possible resolution.

## Pagination

All top-level API resources have support for bulk fetches via "list" API methods. For instance, you can list transactions, wallets. These list API methods share a common structure, taking at least these two parameters: `page` and `limit`.

Argument | Description
--------- | -----------
`page` | Pagination starts at page 1, not at page 0 (page 0 will return the same results as page 1)
`limit` | A limit on the number if objects to be returned. (default 25, max 100)

## Dates

All dates should be passed and will be formatted according with `iso8601` - `YYYY-MM-DDTHH:mm:ss.sssZ` (ex. `2018-04-10T14:48:00.000Z`) 
