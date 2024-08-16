# e-banking_account_bitpay
e_account
usar la api 
https://api.payoneer.com/v4/accounts/{account_id}/balances/{balance_id}/payments/withdraw

Request
import http.client

conn = http.client.HTTPSConnection("api.payoneer.com")

payload = "{\n  \"client_reference_id\": \"withdraw12345\",\n  \"amount\": 30,\n  \"description\": \"some description of transaction\",\n  \"to\": {\n    \"type\": \"bank_id\",\n    \"id\": \"4366181894204341\"\n  }\n}"

headers = {
    'Content-Type': "application/json",
    'Accept': "application/json",
    'Authorization': "Bearer 123"
}

conn.request("POST", "/v4/accounts/{account_id}/balances/{balance_id}/payments/withdraw", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))







Responses

{
  "result": {
    "commit_id": "5a45c76b-687f-46e8-a3f6-1b1d9f6ca406",
    "expires_at": "2020-01-01T09:44:26.4528872Z",
    "type": "withdraw",
    "client_reference_id": "withdraw12345",
    "request_details": {
      "url": "/accounts/2982743/balances/4366181893586952/payments/withdraw",
      "body": {
        "client_reference_id": "withdraw12345",
        "amount": 20000,
        "description": "some description of transaction",
        "target_amount": true,
        "to": {
          "type": "bank_id",
          "id": "4366181894204341"
        }
      }
    },
    "from": {
      "type": "balance",
      "id": "4366181893586952"
    },
    "to": {
      "type": "bank_id",
      "id": "4366181894204341"
    },
    "fees": [
      {
        "type": "transfer_fee",
        "amount": 0,
        "currency": "USD",
        "is_estimated": true
      }
    ],
    "fx": {
      "quote": "5315227",
      "rate": 20000.00,
      "source_currency": "USD",
      "target_currency": "Bsd",
      "is_estimated": true
    },
    "amounts": {
      "charged": {
        "amount": 500,
        "currency": "USD"
      },
      "target": {
        "amount": 20000.00,
        "currency": "Bsd",
        "is_estimated": true
      }
    }
  }
}
