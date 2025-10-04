**<mark>POST api/v2/paygate/payment/card/</mark><br/>**
*Create a card payment<br/><br/>*


#### Request Body schema
*application/json*

| Field           | Type                 | Required | Description                                                                                 | Example                                 |
|-----------------|----------------------|----------|---------------------------------------------------------------------------------------------|-----------------------------------------|
| endpoint        | string <uuid>        | Yes      | Api key                                                                                     | "1dc4441f-38d5-42b5-a705-81958f928462"  |
| amount          | integer              | Yes      | Amount in minor units                                                                       | 1000                                    | 
| currency        | integer              | Yes      | Number code                                                                                 | 978                                     |
| buyer           | object               | Yes      | Buyer at the endpoint in JSON format                                                        | {"remote_id": "string", "ip": "string"} |
| description     | string               | No       | Description                                                                                 | "string"                                |
| client_id       | string               | No       | Transaction id at the endpoint. <br/>Max 255 chars                                          | "string"                                |
| success_url     | string or null <uri> | No       | Redirect URL after success result                                                           | "http://example.com"                    |
| fail_url        | string or null <uri> | No       | Redirect URL after fail result                                                              | "http://example.com"                    |
| notify_url      | string or null <uri> | No       | Notification URL of changed status                                                          | "http://example.com"                    |
| custom_data     | object or null       | No       | Custom params in JSON format                                                                | {"property1": null, "property2": null}  |
| payment_method  | string or null       | No       | The method of payment being used for the transaction. <br/>Used for some types of payments. | "string"                                |
| name            | string               | No       | The customer's name. <br/>Used for some types of payments.                                  | "string"                                |
| email           | string <email>       | No       | The customer's email. <br/>Used for some types of payments.                                 | "user@example.com"                      |
| phone           | string               | No       | The customer's phone number. <br/>Used for some types of payments.                          | "string"                                |
| country         | string               | No       | The customer's country code. <br/>Used for some types of payments.                          | "string"                                |
| browser_info    | object or null       | No       | Browser info in JSON format                                                                 | {"property1": null, "property2": null}  |

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
    "description": "string",
    "client_id": "string",
    "success_url": "http://example.com",
    "fail_url": "http://example.com",
    "notify_url": "http://example.com",
    "custom_data": {
        "property1": null,
        "property2": null
    },
    "payment_method": "string",
    "name": "string",
    "email": "user@example.com",
    "phone": "string",
    "country": "string",
    "browser_info": {
        "accept_header": "string",
        "java_script_enabled": true,
        "language": "string",
        "screen_height": 100,
        "screen_width": 100,
        "time_zone": 100,
        "user_agent": "string",
        "java_enabled": true,
        "screen_color_dept": 100,
        "device_memory": 100,
        "hardware_concurrency": 100,
        "resolution": [
            100
        ],
        "available_resolution": [
            100
        ],
        "timezone_offset": 100,
        "session_storage": 100,
        "local_storage": 100,
        "indexed_db": 100,
        "open_database": 100,
        "cpu_class": "string",
        "has_lied_languages": true,
        "has_lied_resolution": true,
        "has_lied_os": true,
        "has_lied_browser": true,
        "touch_support": [
            "string"
        ],
        "js_fonts": "string",
        "audio_fp": 0.1,
        "fingerprint_hash": "string",
        "location": "string",
        "referer": "string",
        "parent": "string",
        "fp_ip": "string",
        "navigator_platform": "string",
        "regular_plugins": [
            "string"
        ],
        "webgl_vendor": "string",
        "adblock": true
    }
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

  