**<mark>GET /api/v1/paymentgate/payment/info/client/<br/>**
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
        "payment": {
            "amount": 1000,
            "currency": {
                "id": 0,
                "title": "Euro",
                "char_code": "EUR",
                "num_code": 978
            },
            "endpoint": {
                "id": 100,
                "title": "string",
                "created_at": "2024-11-15T09:04:36Z",
                "ips": true,
                "privacy_policy": "string",
                "custom_payment_page": {
                    "id": 100,
                    "page_background": "^#(AAAAAA|AAA)$",
                    "blocks_background": "^#(AAAAAA|AAA)$",
                    "button_color": "^#(AAAAAA|AAA)$",
                    "text_color": "^#(AAAAAA|AAA)$",
                    "privacy_policy": true,
                    "logo": "http://example.com",
                    "endpoint": 100
                }
            },
            "description": "string",
            "status": "create",
            "approved_status": "process",
            "test_mode": true,
            "client_id": "string",
            "created_at": "2024-11-15T09:04:36Z",
            "complete_date": "2024-11-15T09:04:36Z",
            "integration_type": "h2h",
            "merchant_integration_type": "h2h",
            "means_of_payment": {
                "mop_type": {
                    "id": 100,
                    "name": "string",
                    "code": "string"
                },
                "bank_card": {
                    "bin": "string",
                    "pan_mask": "stri",
                    "exp_month": "st",
                    "exp_year": "stri"
                },
                "number": "string",
                "detail": {
                    "property1": null,
                    "property2": null
                }
            },
            "card_token": "string",
            "custom_data": {
                "property1": null,
                "property2": null
            },
            "success_url": "http://example.com",
            "fail_url": "http://example.com",
            "buyer_fee_amount": 0,
            "merchant_fee_amount": 0,
            "means_of_payment_type": {
                "id": 100,
                "name": "string",
                "code": "string"
            },
            "auto_redirect": 100,
            "language": {
                "id": 100,
                "name": "string",
                "code": "string"
            }
        },
        "status": "create",
        "currency": {
            "id": 0,
            "title": "Euro",
            "char_code": "EUR",
            "num_code": 978
        },
        "amount": 1000,
        "created_at": "2024-11-15T09:04:36Z",
        "errors": {
            "property1": null,
            "property2": null
        },
        "parts_tx": [
            {
                "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
                "currency": {
                    "id": 0,
                    "title": "Euro",
                    "char_code": "EUR",
                    "num_code": 978
                },
                "status": "create",
                "amount": 1000,
                "created_at": "2024-11-15T09:04:36Z",
                "errors": {
                    "property1": null,
                    "property2": null
                }
            }
        ],
        "additional_data": {
            "property1": null,
            "property2": null
        },
        "endpoint_logo": "string"
    }
]
```