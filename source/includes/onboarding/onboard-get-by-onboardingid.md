## Get Specific Onboarding Results (GET by Onboarding ID)

### GET /onboard/bundle/{onboardingid}

<!-- RIGHT -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/onboardingapi/onboard/bundle/<ONBOARDINGID> \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'cache-control: no-cache'
```

```csharp
var client = new RestClient("https://api.nelnet.io/onboardingapi/onboard/bundle/<ONBOARDINGID>");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
IRestResponse response = client.Execute(request);
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.nelnet.io/onboardingapi/onboard/bundle/<ONBOARDINGID>");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("tenantid", "10");
xhr.setRequestHeader("servicerid", "1");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = ""

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'cache-control': "no-cache"
    }

conn.request("GET", "onboardingapi,onboard,bundle,<ONBOARDINGID>", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "onboardingId": "string",
        "loanProgramId": "string",
        "tenantId": "0",
        "servicerId": "0",
        "lenderId": "string",
        "itemId": "string",
        "batchId": "string",
        "borrower": {
            "dob": "string",
            "ssn": "string",
            "firstName": "string",
            "middleName": "string",
            "lastName": "string",
            "suffix": "string",
            "addresses": [
                {
                    "city": "string",
                    "state": "string",
                    "street1": "string",
                    "street2": "string",
                    "isPrimary": true,
                    "postalCode": "string",
                    "countryCode": "string"
                }
            ],
            "phoneNumbers": [
                {
                    "isMobile": true,
                    "isPrimary": true,
                    "phoneNumber": "string",
                    "hasCellPhoneConsent": true
                }
            ],
            "emailAddresses": [
                {
                    "isPrimary": true,
                    "emailAddress": "string"
                }
            ],
            "customData": {},
            "externalReferenceId": "string",
            "activePrivacy": false,
            "ecorrAccepted": true,
            "activeMilitary": false
        },
        "loan": {
            "term": 36,
            "amount": 10000,
            "margin": 0,
            "status": "repayment",
            "isActive": true,
            "rateType": "Fixed",
            "interestRate": 3,
            "disbursementDate": "string",
            "firstPaymentDate": "string",
            "paymentScheduleType": "fixed term",
            "investors": [
                {
                    "investorId": "string"
                }
            ]
        },
        "autoDebit": {
            "terms": {
                "type": "Text",
                "content": "string"
            },
            "isActive": true,
            "accountType": "Checking",
            "accountNumber": "string",
            "routingNumber": "string",
            "accountHolderLastName": "string",
            "accountHolderFirstName": "string"
        },
        "bankProfile": {
            "accountType": "Checking",
            "accountNumber": "string",
            "routingNumber": "string",
            "bankProfileName": "string",
            "accountHolderLastName": "string",
            "accountHolderFirstName": "string"
        },
        "cellPhoneConsent": [
            {
                "isMobile": true,
                "hasConsent": true,
                "phoneNumber": "string"
            }
        ],
        "validation": {
            "loan": "Success",
            "borrower": "Success",
            "autoDebit": "Success",
            "completed": "Success",
            "bankProfile": "Success",
            "cellPhoneConsent": "Success"
        },
        "steps": {
            "loan": "Success",
            "borrower": "Success",
            "autoDebit": "Success",
            "completed": "Success",
            "bankProfile": "Success",
            "cellPhoneConsent": "Success"
        },
        "ids": {
            "loanId": "string",
            "borrowerId": "string",
            "autoDebitId": "string",
            "bankProfileId": "string",
            "cellPhoneConsentIds": [
                "string"
            ]
        },
        "errors": [],
        "errorDate": null,
        "createdBy": {},
        "createdDate": "1970-01-01T00:00:00.000Z",
        "updatedBy": {},
        "updatedDate": "1970-01-01T00:00:00.000Z"
    }
}
```

<!-- LEFT -->

**Returns an onboarding request, showing the results of a call to the onboarding endpoint.**

`GET https://api.nelnet.io/onboardingapi/onboard/bundle/{onboardingid}`

### HTTP Request

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
onboardingid | yes | UUID (string) | The onboarding ID created by a (successful) call to the POST /onboard/bundle endpoint.

### HTTP Response

The response payload `ResponseBodyBundle` contains the following.

Field Name | Type | Description
---------- | ------- | -------
data | object | Response object.
data.onboardingId | UUID (string) | A system-generated identifier for the onboarding request.
data.tenantId | string | Identifier for the tenant.
data.servicerId | string | Identifier for the servicer.
data.loanProgramId | UUID (string) | The identifier for the loan program.
data.lenderId | UUID (string) | The identifier for the lender.
data.itemId  | string | The identifier for the onboarding item.
data.batchId | string | The identifier for the onboarding batch.
data.callBackURL | string | Optional callback URL to point an event response to an external source. (Set up for future use.)
|||
borrower | object | The borrower object.
borrower.borrowerId | UUID (string) | A system-generated borrower identifier for the onboarding request.
borrower.firstName | string | The borrower's first name.
borrower.middleName | string | The borrower's middle name (if applicable).
borrower.lastName | string | The borrower's last name.
borrower.suffix | string | The suffix (*Jr.*, *III*, etc.) within the borrower's name (if applicable).
borrower.ssn | string | The borrower's Social Security number, in the 9-digit format without dashes (*111223333*).
borrower.dob | string | The borrower's date of birth, in the YYYY-MM-DD format.
borrower.addresses | array | Array of addresses (at least one address is required).
borrower.phoneNumbers | array | Array of phone numbers (at least one phone number is required).
borrower.emailAddresses | array | Array of email addresses.
borrower.customData | object | Set up for future use.
borrower.activeMilitary | boolean | Indicates whether the borrower is set to receive SCRA benefits.
borrower.activePrivacy | boolean | Indicates whether the borrower's privacy flag is set to true or false.
borrower.externalReferenceId | string | Unique identifier for the borrower record added via the POST onboarding method.
borrower.ecorrAccepted | boolean | Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
|||
loan | object | The loan object.
loan.term | number | The loan's term, in billing cycles. For fixed-payment (rather than fixed-term) loans, `term` may be changed via the payment-schedule calculation that occurs as part of the onboarding process.
loan.amount | number | The loan total amount, in dollars.
loan.interestRate | number | The loan's current interest rate, as a percentage.
loan.margin | number | The loan's margin amount. For fixed-term loans, this should be set to 0.
loan.rateType | enum |  Defaults to *fixed*. Options: Fixed, variable.
loan.paymentScheduleType | enum | Whether the loan's payment schedule is determined by a fixed payment amount or a fixed term (resulting in variable payment amounts over the life of the loan). Options: *fixed term*, *fixed payment*. Defaults to *fixed term*. **Note**: If using *fixed payment*, `paymentAmount` is required and must be numeric and greater than 0.
loan.disbursementDate | string | The date on which the loan funds were dispersed to the borrower, in the YYYY-MM-DD format.
loan.firstPaymentDate | string | The borrower's first payment due date, in the YYYY-MM-DD format.
loan.originationFee | number | The percentage of the dispersement charged to the borrower (in addition to the loan amount) for the origination of the loan.
loan.paymentAmount |  number | The required monthly payment amount, at the time the loan is being onboarded.
loan.status |  enum | The current status of the loan. Defaults to *repayment*. Options: repayment, paid in full, charge off, write off, forbearance, default, fraud, rejected.
loan.externalReferenceId |  string | Unique identifier for the loan record added via the POST onboarding method.
loan.customData | object | Placeholder for any additional data to be stored with the record.
loan.isActive | boolean | Indicates whether the loan is active. Defaults to *true*.
loan.investors | object | Information about investors.
loan.investorId | string | The identifier for the investor associated with the loan.
|||
autoDebit | object | A borrower's auto debit information, if applicable.
autoDebit.routingNumber | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
autoDebit.accountNumber | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
autoDebit.accountType | enum | Options: Checking or Saving.
autoDebit. accountHolderFirstName | string | The account holder's first name.
autoDebit. accountHolderLastName | string | The account holder's last name.
autoDebit.terms | object | The terms and conditions for auto debit agreed to by the borrower.
autoDebit.terms.type |  enum | The type of terms and conditions content included in the auto-debit signup. Options: HTML, ID, Text, URL.
autoDebit.terms.content | string | The content of the terms and conditions disclosure.
autoDebit.isActive | boolean | Defaults to *true*.
|||
bankProfile | object | Contains the bank profile information for borrowers/loans that were onboarded with autodebit information provided. (Including autodebit information in the POST onboarding method automatically creates a bank profile.)
bankProfile. bankProfileName | string | Name of the bank profile created.
bankProfile. routingNumber | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
bankProfile. accountNumber | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
bankProfile. accountType | enum | Options: Checking, savings.
bankProfile. accountHolderFirstName | string | The account holder's first name.
bankProfile. accountHolderLastName | string | The account holder's last name.
|||
cellPhoneConsent | array | Information about cell phone consent collection.
cellPhoneConsent. phoneNumber | string | Borrower's E.164-formatted cell phone number.
cellPhoneConsent. hasConsent | boolean | Indicates whether the borrower has opted in for contact via cell phone.
cellPhoneConsent. isMobile | boolean | Indicates whether the phone number provided is a cell phone/number for a mobile phone.
|||
validation | object | Validation collection.
validation.autoDebit | string | Answers the question: Did the auto debit process validate? Options: *Pending, Skipped, Success, Failure*.
validation.bankProfile | string | Answers the question: Did the bank profile process validate? Options: *Pending, Skipped, Success, Failure*.
validation.borrower | string |  Answers the question: Did the borrower process validate? Options: *Pending, Skipped, Success, Failure*.
validation.cellPhoneConsent | string |  Answers the question: Did the cell phone consent process validate? Options: *Pending, Skipped, Success, Failure*.
validation.loan | string |  Answers the question: Did the loan process validate? Options: *Pending, Skipped, Success, Failure*.
validation.completed | string |  Answers the question: Did the onboarding validate? Options: *Pending, Skipped, Success, Failure*.
|||
steps | object | Step collection — used in validation/processing.
autoDebit | string | Answers the question: Did the auto debit addition complete? Options: *Pending, Skipped, Success, Failure*.
bankProfile | string | Answers the question: Did the bank profile addition complete? (Bank profiles are automatically created if auto debit information is added for a borrower.) Options: *Pending, Skipped, Success, Failure*.
borrower | string | Answers the question: Did the borrower addition complete? Options: *Pending, Skipped, Success, Failure*. (A borrower may not be added but the onboard is still successful, like when added a loan to an existing borrower record.)
cellPhoneConsent | string | Answers the question: Did the addition of a borrower's cell phone data complete? Options: *Pending, Skipped, Success, Failure*
loan | string | Answers the question: Did the additional of the loan complete? Options: *Pending, Skipped, Success, Failure*.
completed | string | Answers the question: Did the onboarding process complete? Options: *Pending, Skipped, Success, Failure*.
|||
ids | object | ID collection.
loanId | string | ID of the loan that was created.
borrowerId | string | ID of the borrower that was created or added to (if onboarding a loan to an existing user).
autoDebitId | string | ID of the autodebit configuration that was created.
bankProfileId | string | ID of the bank profile that was created.
cellPhoneConsentIds | array strings | IDs of the cell phone consent records that was created.
|||
errors | array | Collection of errors potentially returned.
errorDate | string | Date of the last error.
createdBy | string | User who created the onboarding request.
createdDate | string | Date the onboarding record was created.
updatedBy | string | User who updated the onboarding request.
updatedDate | string | Date the onboarding record was updated.