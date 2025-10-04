**<mark>GET api/v2/paygate/payment/info/client/<br/>**
*Get full payment info by id in endpoint (client_id)<br/><br/>*

#### Query parameters

| Field     | Type          | Required | Description                    | Example                                |
|-----------|---------------|----------|--------------------------------|----------------------------------------|
| endpoint  | string <uuid> | Yes      | Endpoint Api key               | "1dc4441f-38d5-42b5-a705-81958f928462" |
| client_id | string <uuid> | Yes      | Transaction id at the endpoint | "f17d7f5c-6b4a-47fd-95eb-08086e250473" | 

#### Response sample

```

STATUS 200

[
  {
    "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
    "payment": {},
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
]
```