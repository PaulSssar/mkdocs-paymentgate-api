**<mark>GET api/v2/paygate/payment/info/</mark><br/>**
*Get full payment info<br/><br/>*

#### Query parameters

| Field    | Type          | Required | Description      | Example                                |
|----------|---------------|----------|------------------|----------------------------------------|
| endpoint | string <uuid> | No       | Endpoint Api key | "1dc4441f-38d5-42b5-a705-81958f928462" |
| tx       | string <uuid> | Yes      | Transaction id   | "f17d7f5c-6b4a-47fd-95eb-08086e250473" | 

#### Response sample
```
STATUS 200

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