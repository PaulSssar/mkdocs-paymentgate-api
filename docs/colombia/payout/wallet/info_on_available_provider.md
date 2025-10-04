**<mark>GET api/v2/paygate/payout/gates/</mark><br/>**
*Get info on available providers for payouts with balances<br/><br/>*

#### Query parameters

| Field    | Type          | Required | Description      | Example                                |
|----------|---------------|----------|------------------|----------------------------------------|
| endpoint | string <uuid> | Yes      | Endpoint Api key | "1dc4441f-38d5-42b5-a705-81958f928462" | 

#### Response sample
```

STATUS 200

[
  {
    "id": 100,
    "balances": [
      {
        "id": 100,
        "name": "string",
        "balance": 1000,
        "currency": {
          "id": 0,
          "title": "Colombian peso",
          "char_code": "COP",
          "num_code": 170
        },
        "rolling_reserve_balance_id": 100
      }
    ]
  }
]
```