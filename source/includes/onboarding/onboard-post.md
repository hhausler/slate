## Onboard a Borrower and/or Loan

### POST /onboard/bundle

<!-- RIGHT -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/onboardingapi/onboard/bundle \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
  "loanProgramId": "string",
  "lenderId": "string",
  "itemId": "string",
  "batchId": "string",
  "callBackURL": "string",
  "borrower": {
    "borrowerId": "string",
    "firstName": "string",
    "middleName": "string",
    "lastName": "string",
    "suffix": "string",
    "ssn": "string",
    "dob": "string",
    "addresses": [
      {
        "street1": "string",
        "street2": "string",
        "city": "string",
        "state": "string",
        "postalCode": "string",
        "countryCode": "string",
        "isPrimary": true
      }
    ],
    "phoneNumbers": [
      {
        "phoneNumber": "string",
        "isPrimary": true,
        "isMobile": true,
        "hasCellPhoneConsent": true
      }
    ],
    "emailAddresses": [
      {
        "emailAddress": "string",
        "isPrimary": true
      }
    ],
    "customData": {},
    "activeMilitary": true,
    "activePrivacy": true,
    "externalReferenceId": "string",
    "ecorrAccepted": true
  },
  "loan": {
    "term": 0,
    "amount": 0,
    "interestRate": 0,
    "margin": 0,
    "rateType": "Fixed",
    "disbursementDate": "string",
    "firstPaymentDate": "string",
    "originationFee": 0,
    "paymentAmount": 0,
    "status": "repayment",
    "externalReferenceId": "string",
    "customData": {},
    "isActive": true
    "investors": [
      {
        "investorId": "string"
      }
    ]
  },
  "autoDebit": {
    "routingNumber": "string",
    "accountNumber": "string",
    "accountType": "Checking",
    "accountHolderFirstName": "string",
    "accountHolderLastName": "string",
    "terms": {
      "type": "HTML",
      "content": "string"
    },
    "isActive": true
  }
}
```

```csharp
var client = new RestClient("https://api.nelnet.io/onboardingapi/onboard/bundle");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddParameter("undefined", "{\n    \"loanProgramId\": \"string\",\n    \"lenderId\": \"string\",\n    \"itemId\": \"string\",\n    \"batchId\": \"string\",\n    \"callBackURL\": \"string\",\n    \"borrower\": {\n        \"firstName\": \"string\",\n        \"middleName1\": \"string\",\n        \"lastName\": \"string\",\n        \"suffix1\": \"string\",\n        \"externalReferenceId\": \"string\",\n        \"ssn\": \"string\",\n        \"dob\": \"string\",\n        \"addresses\": [\n            {\n                \"street1\": \"string\",\n                \"street2\": \"string\",\n                \"city\": \"string\",\n                \"state\": \"string\",\n                \"postalCode\": \"string\",\n                \"countryCode\": \"string\",\n                \"isPrimary\": true\n            }\n        ],\n        \"phoneNumbers\": [\n            {\n                \"phoneNumber\": \"string\",\n                \"isPrimary\": true,\n                \"isMobile\": true,\n                \"hasCellPhoneConsent\": true\n            }\n        ],\n        \"emailAddresses\": [\n            {\n                \"emailAddress\": \"string\",\n                \"isPrimary\": true\n            }\n        ],\n        \"customData\": {\n            \"string\": \"any\"\n        },\n        \"activeMilitary\": false,\n        \"activePrivacy\": true,\n        \"ecorrAccepted\": true\n    },\n    \"loan\": {\n        \"externalReferenceId\": \"string\",\n        \"term\": 36,\n        \"amount\": 10000,\n        \"interestRate\": 3,\n        \"margin\": 0,\n        \"rateType\": \"Fixed\",\n        \"disbursementDate\": \"string\",\n        \"firstPaymentDate\": \"string\",\n        \"status\": \"repayment\",\n        \"customData\": {\n            \"string\": \"any\"\n        },\n        \"isActive\": true\n    },\n    \"autoDebit\": {\n        \"routingNumber\": \"string\",\n        \"accountNumber\": \"string\",\n        \"accountType\": \"Checking\",\n        \"accountHolderFirstName\": \"string\",\n        \"accountHolderLastName\": \"string\",\n        \"terms\": {\n            \"type\": \"Text\",\n            \"content\": \"string\"\n        }\n    }\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript
var data = JSON.stringify({
  "loanProgramId": "string",
  "lenderId": "string",
  "itemId": "string",
  "batchId": "string",
  "callBackURL": "string",
  "borrower": {
    "firstName": "string",
    "middleName1": "string",
    "lastName": "string",
    "suffix1": "string",
    "externalReferenceId": "string",
    "ssn": "string",
    "dob": "string",
    "addresses": [
      {
        "street1": "string",
        "street2": "string",
        "city": "string",
        "state": "string",
        "postalCode": "string",
        "countryCode": "string",
        "isPrimary": true
      }
    ],
    "phoneNumbers": [
      {
        "phoneNumber": "string",
        "isPrimary": true,
        "isMobile": true,
        "hasCellPhoneConsent": true
      }
    ],
    "emailAddresses": [
      {
        "emailAddress": "string",
        "isPrimary": true
      }
    ],
    "customData": {
      "string": "any"
    },
    "activeMilitary": false,
    "activePrivacy": true,
    "ecorrAccepted": true
  },
  "loan": {
    "externalReferenceId": "string",
    "term": 36,
    "amount": 10000,
    "interestRate": 3,
    "margin": 0,
    "rateType": "Fixed",
    "disbursementDate": "string",
    "firstPaymentDate": "string",
    "status": "repayment",
    "customData": {
      "string": "any"
    },
    "isActive": true
  },
  "autoDebit": {
    "routingNumber": "string",
    "accountNumber": "string",
    "accountType": "Checking",
    "accountHolderFirstName": "string",
    "accountHolderLastName": "string",
    "terms": {
      "type": "Text",
      "content": "string"
    }
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/onboardingapi/onboard/bundle");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "{\n    \"loanProgramId\": \"string\",\n    \"lenderId\": \"string\",\n    \"itemId\": \"string\",\n    \"batchId\": \"string\",\n    \"callBackURL\": \"string\",\n    \"borrower\": {\n        \"firstName\": \"string\",\n        \"middleName1\": \"string\",\n        \"lastName\": \"string\",\n        \"suffix1\": \"string\",\n        \"externalReferenceId\": \"string\",\n        \"ssn\": \"string\",\n        \"dob\": \"string\",\n        \"addresses\": [\n            {\n                \"street1\": \"string\",\n                \"street2\": \"string\",\n                \"city\": \"string\",\n                \"state\": \"string\",\n                \"postalCode\": \"string\",\n                \"countryCode\": \"string\",\n                \"isPrimary\": true\n            }\n        ],\n        \"phoneNumbers\": [\n            {\n                \"phoneNumber\": \"string\",\n                \"isPrimary\": true,\n                \"isMobile\": true,\n                \"hasCellPhoneConsent\": true\n            }\n        ],\n        \"emailAddresses\": [\n            {\n                \"emailAddress\": \"string\",\n                \"isPrimary\": true\n            }\n        ],\n        \"customData\": {\n            \"string\": \"any\"\n        },\n        \"activeMilitary\": false,\n        \"activePrivacy\": true,\n        \"ecorrAccepted\": true\n    },\n    \"loan\": {\n        \"externalReferenceId\": \"string\",\n        \"term\": 36,\n        \"amount\": 10000,\n        \"interestRate\": 3,\n        \"margin\": 0,\n        \"rateType\": \"Fixed\",\n        \"disbursementDate\": \"string\",\n        \"firstPaymentDate\": \"string\",\n        \"status\": \"repayment\",\n        \"customData\": {\n            \"string\": \"any\"\n        },\n        \"isActive\": true\n    },\n    \"autoDebit\": {\n        \"routingNumber\": \"string\",\n        \"accountNumber\": \"string\",\n        \"accountType\": \"Checking\",\n        \"accountHolderFirstName\": \"string\",\n        \"accountHolderLastName\": \"string\",\n        \"terms\": {\n            \"type\": \"Text\",\n            \"content\": \"string\"\n        }\n    }\n}"

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Content-Type': "application/json",
    'cache-control': "no-cache"
    }

conn.request("POST", "onboardingapi,onboard,bundle", payload, headers)

res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
    "data": {
        "onboardingId": "UUID",
        "itemId": "string",
        "batchId": "string",
        "createdDate": "1970-01-01T00:00:00.000Z",
        "paymentScheduleType": "fixed term"
    }
}
```

<!-- LEFT -->

**Adds a new borrower and/or a loan to an existing borrower/customer record. Also adds bank profile, auto debit and cell phone consent information for a borrower.**

Use this endpoint to add a new loan and a new borrower to the system. The borrower object's fields are required unless you want to add a new loan to an existing borrower's record. To add a new loan, pass a borrowerID and the rest of the borrower object's fields will be skipped.

<aside class="warning">
This endpoint is not meant to update an existing borrower's information (name, demographic information, etc.).
</aside>

You can also add auto debit and cell phone consent information for a new borrower.

<aside class="notice">
If auto debit information is included via the auto debit object, a bank profile is also automatically set up for the borrower.
</aside>

### HTTP Request

`POST https://api.nelnet.io/onboardingapi/onboard/bundle`

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
loanProgramId | yes | UUID (string) | The identifier for the loan program.
lenderId | yes | UUID (string) | The identifier for the lender.
itemId | no | string | The identifier for the onboarding item. This can be queried once posted.
batchId | no | string | The identifier for the onboarding batch. This can be queried once posted.
callBackURL | no | string | Optional callback URL to point an event response to an external source.
|||
borrower | yes (see description) | object | The borrower record is required if onboarding a new borrower and a new loan.
borrower.borrowerId | no | UUID (string) | To add a new loan to an existing borrower, enter the borrower ID for that borrower.
borrower.firstName | yes | string | Required for a new borrower. The borrower's first name.
borrower.middleName | no | string | The borrower's middle name (if applicable).
borrower.lastName | yes | string | Required for a new borrower. The borrower's last name.
borrower.suffix | no | string | The suffix (*Jr.*, *III*, etc.) within the borrower's name (if applicable).
borrower.ssn | yes | string | The borrower's Social Security number, in the 9-digit format without dashes (*111223333*).
borrower.dob | yes | string | The borrower's date of birth, in the YYYY-MM-DD format.
borrower.addresses | yes | array | Array of addresses (at least one address is required). See the [borrower addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.phoneNumbers | yes | array | Array of phone numbers (at least one phone number is required). See the [borrower phone numbers table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.emailAddresses | yes | array | Array of email addresses. See the [borrower email addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.customData | yes | object | Set up for future use.
borrower.activeMilitary | yes | boolean | Indicates whether the borrower is set to receive SCRA benefits.
borrower.activePrivacy | yes | boolean | Indicates whether the borrower's privacy flag is set to true or false.
borrower.externalReferenceId | yes | string | Unique identifier for the borrower record — can be set to anything, but must be unique.
borrower.ecorrAccepted | yes | boolean | Defaults to *true*. Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
|||
loan | yes | object | The loan object is required for all calls to this endpoint.
loan.term | yes | number | The loan's term, in billing cycles. For fixed-payment (rather than fixed-term) loans, `term` may be changed via the payment-schedule calculation that occurs as part of the onboarding process.
loan.amount | yes | number | The loan total amount, as of today, in dollars.
loan.interestRate | yes | number | The loan's current interest rate, as a percentage.
loan.margin | no | number | The loan's margin amount. For fixed-term loans, this should be set to 0.
loan.rateType | yes | enum |  Whether the loan's rate changes over time (variable) or is constant (fixed). Defaults to *fixed*. Options: *fixed*, *variable*.
loan.paymentScheduleType | no | enum | Whether the loan's payment schedule is determined by a fixed payment amount or a fixed term (resulting in variable payment amounts over the life of the loan). Options: *fixed term*, *fixed payment*. Defaults to *fixed term*. **Note**: If using *fixed payment*, `paymentAmount` is required and must be numeric and greater than 0.
loan.disbursementDate | yes | string | The date on which the loan funds were disbursed to the borrower, in the YYYY-MM-DD format. Must be today or any date before today (can't be in the future).
loan.firstPaymentDate | yes | string | The borrower's first payment due date, in the YYYY-MM-DD format. Must be after the `disbursementDate` **and** after today (can't be in the past).
loan.originationFee | yes | number | The amount of the disbursement charged to the borrower (in addition to the loan amount) for the origination of the loan.
loan.paymentAmount | yes | number | The minimum required monthly payment amount, at the time the loan is being onboarded.
loan.status | yes | enum | The current status of the loan. Defaults to *repayment*. Options: *repayment, paid in full, charge off, write off, forbearance, default, fraud, rejected*.
loan.externalReferenceId | no | string | Unique identifier for the loan record — can be set to anything, but must be unique.
loan.customData | yes | object | Placeholder for any additional data to be stored with the record.
loan.isActive | yes | boolean | Indicates whether the loan is active. Defaults to *true*.
loan.investors | no | object | Information about investors.
loan.investorId | no | string | The identifier for the investor associated with the loan.
|||
autoDebit | no | object | If used, the method also creates a bank profile that's populated with the autodebit information.
autoDebit.routingNumber | yes | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
autoDebit.accountNumber | yes | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
autoDebit.accountType | yes | enum | Account type for the account used by autodebit. Options: *Checking*, *Saving*.
autoDebit. accountHolderFirstName | yes | string | The account holder's first name.
autoDebit. accountHolderLastName | yes | string | The account holder's last name.
autoDebit.terms | no | object | The terms and conditions for autodebit agreed to by the borrower.
autoDebit.terms.type | yes | enum | The type of terms and conditions content included in the autodebit signup. Options: *HTML, ID, Text, URL.*
autoDebit.terms.content | yes | string | The content of the terms and conditions disclosure.
autoDebit.isActive | yes | boolean | Set to *true* to onboard a loan with an active autodebit profile. Set to *false* to onboard a loan with autodebit information that not currently in use - the result will be that the borrower has an autodebit profile associated, but that autodebit will not be used to collect payment unless it's activated.

### HTTP Response
Field Name | Type | Description
---------- | ------- | ------- | -------
onboardingId | UUID (string) | A system-generated identifier for the onboarding request.
itemId | string | The itemID for the onboarding request that was added in the onboarding add method.
batchId | string | The batchID for the onboarding request that was added in the onboarding add method.
createdDate | string | The date that the borrower and/or loan was added/onboarded.
