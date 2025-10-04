### **Test cards**
- 4100 0000 0000 0001 - Visa / Success payment (non 3DS)
- 4200 0000 0000 0000 - Visa / Unsuccess payment (non 3DS)
- 5140 0000 0000 0000 - MC / Success payment (non 3DS)
- 5280 0000 0000 0000 - MC / Unsuccess payment (non 3DS)
- 4022 0501 0000 0000 - Visa / 3DS
- 5132 5626 0000 0011 - MC / 3DS
- 5132 5626 0000 1111 – correct 3DS code

| Status           | 	Payment | 	Payout	 | Final	 | Description                                                                                                                                                                             |
|------------------|----------|----------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| create           | yes	     | yes	     | no	    | First status when transaction created.                                                                                                                                                  |
| moderation       | 	no	     | yes      | 	no	   | Only for payouts with moderation.                                                                                                                                                       |
| queue            | no       | yes      | no     | Only if payout in queue and waits send to provider.                                                                                                                                     |
| process          | 	yes     | 	yes     | 	no    | 	Transaction sent to provider and wait final status. Each 5 minutes system tries to check status from provider.                                                                         |
| waiting          | 	yes     | 	yes     | 	no    | 	Transaction sent to provider and wait final status. System don't check status from provider, only waits callbacks.                                                                     |
| preauth          | 	yes     | 	no      | 	no    | 	Only for preauth payments. (In work)                                                                                                                                                   |
| success          | 	yes     | 	yes     | 	yes*  | 	Final success transaction.                                                                                                                                                             |
| canceled         | 	yes     | 	yes     | 	yes*  | 	Cancelled by our system or by provider.                                                                                                                                                |
| canceled_timeout | 	yes     | 	yes     | 	yes*  | 	Cancelled by our system after timeout (48 hours).                                                                                                                                      |
| error            | 	yes     | 	yes     | 	yes*  | 	Something went wrong. Internal error or error from provider.                                                                                                                           |
| failed           | 	yes     | 	yes     | 	yes*  | 	Failed by provider.                                                                                                                                                                    |
| antifraud_error  | 	yes     | 	no      | 	yes   | 	Error from antifraud checking.                                                                                                                                                         |
| reversal         | 	yes     | 	yes     | 	yes*  | 	Reversal by provider.                                                                                                                                                                  |
| charge_back      | 	yes     | 	no      | 	yes*  | 	Charge back by provider.                                                                                                                                                               |
| unknown          | 	yes     | 	yes     | 	no    | 	If something went wrong with provider, system set unknown status and tries to wait, every 5 minutes checks transaction with provider. After timeout sets reversal or canceled_timeout. |

- The final payment statuses may changed if the provider sends a new one. In such a case, you will receive a callback notification, and our technical support team will also inform you manually.
- The final payout statuses do not change, however, if there is a discrepancy with the provider, our technical support team will notify you manually, and such cases will be handled separately.

### **Authentication for paymentgate**

<mark>**Header parameter name**: API-Sign<mark>

Header parameter for signing API-Sign is hash (SHA256) of string with format: **endpoint_secret_key+""+data_string**.

Where:

- endpoint_secret_key - this is secret key for signing queries. Created at endpoint settings in merchant account.
- data_string - request data formatted as json.

*Can be with delimeter spaces and without them, but not mix of both*

Data example:
```
- endpoint_secret_key = '123'
- Request data: {"amount": 1000, "email": "test@test.com"}
```
Signature example without spaces:
```
- Hash string: 123{"amount":1000,"email":"test@test.com"}
- Signature: 6132c86940bde29d50baa8ced579f8e4d00178fbc5141f7ed431dc03adfa5e4e
```
Signature example with spaces:
```
Hash string: 123{"amount": 1000, "email": "test@test.com"} 
Signature: cae7b5f32d90e394eb03bb923a858502ac7b232300b780a1b78e99f7c888236a
```