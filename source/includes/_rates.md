# Rates

## Return your acquiring/processing rates

> GET https://cryptoprocessing.io/api/v1/rates/:direction?gateway=cryptocard

### Attributes:

Attribute | Description
--------- | -----------
`gateway` | Required, available options: "cryptocard", "cryptoprocessing", or "wire"
`direction` | Required, available options: "acquiring", "processing"

> Example Request

```shell
curl "https://cryptoprocessing.io/api/v1/rates/acquiring?gateway=cryptocard" \
  -H "Authorization: <jwt token>" \
  -X GET
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "EUR": {
            "BTC": 6189.737373737374
        },
        "USD": {
            "BTC": 7071.131313131313
        }
    }
}
```
