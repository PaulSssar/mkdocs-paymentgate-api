**<mark>POST api/v2/paygate/payout/wallet/</mark><br/>**
*Create a payout by wallet<br/><br/>*


#### Request Body schema
*application/json*

| Field          | Type                 | Required    | Description                                                                                                       | Example                                 |
|----------------|----------------------|-------------|-------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
| endpoint       | string <uuid>        | Yes         | Api key                                                                                                           | "1dc4441f-38d5-42b5-a705-81958f928462"  |
| amount         | integer              | Yes         | Amount in minor units                                                                                             | 1000                                    | 
| currency       | integer              | Yes         | Number code                                                                                                       | 170                                     |
| buyer          | object               | Yes         | Buyer at the endpoint in JSON format                                                                              | {"remote_id": "string", "ip": "string"} |
| module         | integer              | No          | Payout module ID                                                                                                  | 100                                     |
| description    | string               | No          | Description                                                                                                       | "string"                                |
| client_id      | string               | No          | Transaction id at the endpoint. <br/>Max 255 chars                                                                | "string"                                |
| notify_url     | string or null <uri> | No          | Notification URL of changed status                                                                                | "http://example.com"                    |
| router_data    | object or null       | No          | Router data in JSON format                                                                                        | {"property1": null, "property2": null}  |
| custom_data    | object or null       | No          | Custom params in JSON format                                                                                      | {"property1": null, "property2": null}  |
| moderated      | boolean or null      | No          | Is payout moderated? <b>Default: True</b>                                                                         | True                                    |
| holder         | string               | Yes         | The customer's name                                                                                               | "John Smith"                            |
| account_number | string               | Yes         | The customer's account number                                                                                     | "string"                                |


#### Request sample<br/>
```
{
    "endpoint": "1dc4441f-38d5-42b5-a705-81958f928462",
    "amount": 1000,
    "currency": 170,
    "buyer": {
        "remote_id": "string",
        "ip": "string"
    },
    "module": 100,
    "description": "string",
    "client_id": "string",
    "notify_url": "http://example.com",
    "router_data": {
        "property1": null,
        "property2": null
    },
    "custom_data": {
        "property1": null,
        "property2": null
    },
    "holder": "John Smith",
    "account_number": "string",
}
```

#### Response sample
```

STATUS 201

{
    "tx": {
        "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
        "payout": {},
        "status": "create",
        "currency": {
          "id": 0,
          "title": "TRY",
          "char_code": "TRY",
          "num_code": 949
        },
        "amount": 1000,
        "created_at": "2000-01-01T00:00:00Z",
        "errors": {},
        "parts_tx": [],
        "additional_data": {},
        "endpoint_logo": "string"
    }
}
```