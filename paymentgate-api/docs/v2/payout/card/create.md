**<mark>POST api/v2/paygate/payout/card/</mark><br/>**
*Create a card payout<br/><br/>*


#### Request Body schema
*application/json*

| Field          | Type                   | Required | Description                                                                                    | Example                                 |
|----------------|------------------------|----------|------------------------------------------------------------------------------------------------|-----------------------------------------|
| endpoint       | string <uuid>          | Yes      | Api key                                                                                        | "1dc4441f-38d5-42b5-a705-81958f928462"  |
| amount         | integer                | Yes      | Amount in minor units                                                                          | 1000                                    | 
| currency       | integer                | Yes      | Number code                                                                                    | 978                                     |
| buyer          | object                 | Yes      | Buyer at the endpoint in JSON format                                                           | {"remote_id": "string", "ip": "string"} |
| module         | integer                | No       | Payout module ID                                                                               | 100                                     |
| description    | string                 | No       | Description                                                                                    | "string"                                |
| client_id      | string                 | No       | Transaction id at the endpoint. <br/>Max 255 chars                                             | "string"                                |
| notify_url     | string or null <uri>   | No       | Notification URL of changed status                                                             | "http://example.com"                    |
| router_data    | object or null         | No       | Router data in JSON format                                                                     | {"property1": null, "property2": null}  |
| custom_data    | object or null         | No       | Custom params in JSON format                                                                   | {"property1": null, "property2": null}  |
| moderated      | boolean or null        | No       | Is payout moderated? <b>Default: True</b>                                                      | True                                    |
| payment_method | string or null         | No       | The method of payment being used for the transaction. <br/>Used for some types of withdrawals. | "string"                                |
| name           | string                 | No       | The customer's name. <br/>Used for some types of withdrawals.                                  | "string"                                |
| first_name     | string                 | No       | The customer's first name. <br/>Used for some types of withdrawals.                            | "string"                                |
| last_name      | string                 | No       | The customer's last name. <br/>Used for some types of withdrawals.                             | "string"                                |
| holder         | string                 | No       | The customer's holder. <br/>Used for some types of withdrawals.                             | "string"                                |
| email          | string <email>         | No       | The customer's email. <br/>Used for some types of withdrawals.                                 | "user@example.com"                      |
| phone          | string                 | No       | The customer's phone number. <br/>Used for some types of withdrawals.                          | "string"                                |
| country        | string                 | No       | The customer's country code. <br/>Used for some types of withdrawals.                          | "string"                                |
| pan            | string                 | No       | Card primary account number (PAN). <br/>Used for some types of withdrawals.                    | "string"                                |
| card_token     | string                 | No       | Card token in our system. <br/>Used for some types of withdrawals.                             | "string"                                |

#### Request sample<br/>
```
{
    "endpoint": "1dc4441f-38d5-42b5-a705-81958f928462",
    "amount": 1000,
    "currency": 978,
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
    "payment_method": "string",
    "name": "string",
    "first_name": "string",
    "last_name": "string",
    "holder": "string",
    "email": "user@example.com",
    "phone": "string",
    "country": "string",
    "pan": "string",
    "card_token": "string"
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
          "title": "Euro",
          "char_code": "EUR",
          "num_code": 978
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