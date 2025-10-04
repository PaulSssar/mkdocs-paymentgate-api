**<mark>POST api/v1/paymentgate/payment/simple/</mark><br/>**
*Record payment registration in system and return payment info with redirect link<br/><br/>*


#### Request Body schema
*application/json*

| Field             | Type                 | Required  | Description                                              | Example                                 |
|-------------------|----------------------|-----------|----------------------------------------------------------|-----------------------------------------|
| endpoint          | string <uuid>        | Yes       | Api key                                                  | "1dc4441f-38d5-42b5-a705-81958f928462"  |
| amount            | integer              | Yes       | Amount in minor units                                    | 1000                                    | 
| currency          | integer              | Yes       | Number code                                              | 810                                     |
| description       | string               | No        | Description                                              | "string"                                |
| client_id         | string               | No        | Transaction id at the endpoint. <br/>Max 255 chars       | "string"                                |
| success_url       | string or null <uri> | No        | Redirect URL after success result                        | "http://example.com"                    |
| fail_url          | string or null <uri> | No        | Redirect URL after fail result                           | "http://example.com"                    |
| notify_url        | string or null <uri> | No        | Notification URL of changed status                       | "http://example.com"                    |
| router_data       | object or null       | No        | Router data                                              | {"property1": null, "property2": null}  |
| custom_data       | object or null       | No        | Custom params in JSON format                             | {"property1": null, "property2": null}  |
| payment_method    | string               | No        | Payment method type                                      | "string"                                |
| tx_payment_method | string or null       | No        | Additional payment method                                | "string"                                |
| additional_data   | object               | No        | Additional data                                          | {"property1": null, "property2": null}  |
| auto_redirect     | integer              | Default=0 | Auto redirect in seconds                                 | 100                                     |
| buyer_id          | string               | No        | Buyer id at the endpoint (deprecated)<br/>Max chars 255. | "string"                                |
| buyer             | object               | No        | Buyer at the endpoint                                    | {"remote_id": "string", "ip": "string"} |

#### Request sample<br/>
```
{
    "endpoint": "1dc4441f-38d5-42b5-a705-81958f928462",
    "amount": 1000,
    "currency": 100,
    "description": "string",
    "client_id": "string",
    "success_url": "http://example.com",
    "fail_url": "http://example.com",
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
    "tx_payment_method": "string",
    "additional_data": {
        "property1": null,
        "property2": null
    },
    "auto_redirect": 100,
    "buyer_id": "string",
    "buyer": {
        "remote_id": "string",
        "ip": "string"
    }
}
```

#### Response sample
```

STATUS 200

{
    "redirect_url": "http://example.com",
    "info": {
        "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
        "payment": {},
        "status": "create",
        "currency": {},
        "amount": 1000,
        "created_at": "2024-11-15T09:04:36Z",
        "errors": {},
        "parts_tx": [],
        "additional_data": {},
        "endpoint_logo": "string"
    },
    "qr_code": {
        "qrcode": "string",
        "beneficiary": "string",
        "format": "string"
    },
    "p2p_wallet_data": {
        "target_account_number": "string",
        "bank_name": "string",
        "holder": "string",
        "valid_till": "2024-11-15T09:04:36Z",
        "tll": "14:15:22Z"
    },
    "p2p_card_data": {
        "target_card_number": "string",
        "bank_name": "string",
        "holder": "string",
        "valid_till": "2024-11-15T09:04:36Z",
        "tll": "14:15:22Z"
    },
    "pay_data": "string"
}
```

  