**<mark>POST /api/v1/paymentgate/callback/info/payment/</mark><br/>**
*Example of the structure of all payment callback requests<br/><br/>*


#### Request Body schema 
*application/json*

| Field           | Type                                               | Required | Example                                |
|-----------------|----------------------------------------------------|----------|----------------------------------------|
| tx              | string <uuid>                                      | Yes      | "1dc4441f-38d5-42b5-a705-81958f928462" |
| payment         | object (CallbackPaymentGatePayment)                | Yes      |                                        | 
| status          | string (TransferStatus)*                           | No       | "create"                               |
| currency        | object                                             | Yes      |                                        |
| amount          | integer <int64>                                    | No       |                                        |
| created_at      | string <date-time> (Created date)                  | No       | "2024-11-15T09:04:36Z"                 |
| errors          | object or null                                     | No       |                                        |
| settings        | object (CallbackPaymentGatePaymentGatewaySettings) | Yes      |                                        |
| parts_tx        | Array of objects (TransactionShort)                | Yes      |                                        |
| additional_data | object or null                                     | No       | {"property1": null, "property2": null} |

*Enum:

- create - Created
- moderation - Moderation
- process - In process
- queue - In queue
- waiting - Waiting
- preauth - In preauth
- success - Success
- canceled - Cancelled
- canceled_timeout - Cancelled by timeout
- error - Error
- failed - Failed
- antifraud_error - Antifraud error
- reversal - Reversal
- unknown - Unknown

#### Request sample<br/>
```
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
        "description": "string",
        "status": "create",
        "test_mode": true,
        "client_id": "string",
        "created_at": "2024-11-15T09:04:36Z",
        "complete_date": "2024-11-15T09:04:36Z",
        "integration_type": "h2h",
        "means_of_payment": {
            "mop_type": {
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
        "fee_amount": 100,
        "merchant_fee_amount": 100,
        "buyer_fee_amount": 100,
        "means_of_payment_type": {
            "name": "string",
            "code": "string"
        },
        "auto_redirect": 100
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
    "settings": {
        "id": 100,
        "balances": [
            {
                "name": "string",
                "balance": 100
            }
        ]
    },
    "parts_tx": [
        {
            "tx": "f17d7f5c-6b4a-47fd-95eb-08086e250473",
            "currency": {
                "id": 0,
                "title": "Euro",
                "char_code": "EUR",
                "num_code": 978
            }
        }
    ],
    "additional_data": {
        "property1": null,
        "property2": null
    }
}
```

#### Response sample
```

STATUS 200

No response body
```