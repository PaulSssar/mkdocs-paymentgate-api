**<mark>POST api/v2/paygate/payment/wallet/</mark><br/>**
*Create a payment by wallet<br/><br/>*


#### Request Body schema
*application/json*

| Field           | Type                 | Required | Description                                                                                                          | Example                                 |
|-----------------|----------------------|----------|----------------------------------------------------------------------------------------------------------------------|-----------------------------------------|
| endpoint        | string <uuid>        | Yes      | Api key                                                                                                              | "1dc4441f-38d5-42b5-a705-81958f928462"  |
| amount          | integer              | Yes      | Amount in minor units                                                                                                | 1000                                    | 
| currency        | integer              | Yes      | Number code                                                                                                          | 170                                     |
| buyer           | object               | Yes      | Buyer at the endpoint in JSON format                                                                                 | {"remote_id": "string", "ip": "string"} |
| description     | string               | No       | Description                                                                                                          | "string"                                |
| client_id       | string               | No       | Transaction id at the endpoint. <br/>Max 255 chars                                                                   | "string"                                |
| success_url     | string or null <uri> | No       | Redirect URL after success result                                                                                    | "http://example.com"                    |
| fail_url        | string or null <uri> | No       | Redirect URL after fail result                                                                                       | "http://example.com"                    |
| notify_url      | string or null <uri> | No       | Notification URL of changed status                                                                                   | "http://example.com"                    |
| custom_data     | object or null       | No       | Custom params in JSON format                                                                                         | {"property1": null, "property2": null}  |
| payment_method  | string or null       | Yes      | The method of payment being used for the transaction. <br/><b>May be:</b> <i>nequi, bancolombia, transfiya, pse</i>  | "pse"                                   |
| name            | string               | Yes      | The customer's name                                                                                                  | "John Smith"                            |
| email           | string <email>       | Yes      | The customer's email                                                                                                 | "user@example.com"                      |
| phone           | string               | Yes      | The customer's phone number in international format (E164)                                                           | "+571111111111"                         |
| country         | string               | Yes      | The customer's country code                                                                                          | "COL"                                   |
| document_number | string               | Yes      | The customer's official identification number assigned by a government authority                                     | "string"                                |
| document_type   | string               | Yes      | The customer's document type. <br/>Common types include national ID, or driver's license                             | "CC"                                    |


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
    "description": "string",
    "client_id": "string",
    "success_url": "http://example.com",
    "fail_url": "http://example.com",
    "notify_url": "http://example.com",
    "custom_data": {
        "property1": null,
        "property2": null
    },
    "payment_method": "pse",
    "name": "John Smith",
    "email": "user@example.com",
    "phone": "+571111111111",
    "country": "COL",
    "document_number": "string",
    "document_type": "CC"
}
```

#### Response sample
```

STATUS 201

{
    "redirect_url": "http://example.com",
    "info": {
        "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
        "payment": {},
        "status": "create",
        "currency": {
          "id": 0,
          "title": "Colombian peso",
          "char_code": "COP",
          "num_code": 170
        },
        "amount": 1000,
        "created_at": "2000-01-01T00:00:00Z",
        "errors": {},
        "parts_tx": [],
        "additional_data": {},
        "endpoint_logo": "string"
    },
    "qr_code": {
        "qrcode": "string",
        "beneficiary": "string",
        "format": "string",
        "copypaste": "string"
    },
    "p2p_wallet_data": {
        "target_account_number": "string",
        "bank_name": "string",
        "holder": "string",
        "valid_till": "2000-01-01T00:00:00Z",
        "tll": "00:00:00Z"
    },
    "p2p_card_data": {
        "target_account_number": "string",
        "bank_name": "string",
        "holder": "string",
        "valid_till": "2000-01-01T00:15:00Z",
        "tll": "00:15:00Z"
    },
    "pay_data": "string"
}
```