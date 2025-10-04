**<mark>GET api/v2/paygate/payout/info/</mark><br/>**
*Get full payout info<br/><br/>*

#### Query parameters

| Field    | Type          | Required | Description      | Example                                |
|----------|---------------|----------|------------------|----------------------------------------|
| endpoint | string <uuid> | No       | Endpoint Api key | "1dc4441f-38d5-42b5-a705-81958f928462" |
| tx       | string <uuid> | Yes      | Transaction id   | "f17d7f5c-6b4a-47fd-95eb-08086e250473" | 

#### Response sample
```
STATUS 200

{
    "tx": {
        "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
        "payout": {},
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
    }
}
```