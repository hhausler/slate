<!--Endpoint introduction -->
## Get Bundles of Onboarding Results (GET by Onboarding Bundle)

### GET /onboard/bundles

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/onboardingapi/onboard/bundles?limit=1' \
  -H 'Authorization: <BEARER TOKEN>' \
  -H 'Host: api.nelnet.io' \
  -H 'servicerid: 2' \
  -H 'tenantid: 314'
```

```csharp
var client = new RestClient("https://development.nelnet.io/onboardingapi/onboard/bundles?limit=1");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "Bearer <ACCESS TOKEN>");
request.AddParameter("text/plain", "",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = "";

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://development.nelnet.io/onboardingapi/onboard/bundles?limit=1");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "Bearer <ACCESS TOKEN>");

xhr.send(data);
```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("development.nelnet.io")
payload = ''
headers = {
  'tenantid': '314',
  'servicerid': '2',
  'Authorization': 'Bearer <ACCESS TOKEN>'
}
conn.request("GET", "/onboardingapi/onboard/bundles?limit=1", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "onboardingId": "c5ccb7e8-70fb-496f-a8d8-4dc6f70e8654",
            "loanProgramId": "50023379-ef51-4262-b428-84865cd20f41",
            "tenantId": "314",
            "servicerId": "2",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "itemId": null,
            "batchId": null,
            "callBackURL": null,
            "borrower": {
                "dob": "1981-01-21",
                "ssn": "737370021",
                "suffix": "",
                "lastName": "Doo",
                "walletId": "",
                "addresses": [
                    {
                        "city": "Coolsville",
                        "state": "OH",
                        "street1": "123 Mystery Ln",
                        "street2": "",
                        "isPrimary": true,
                        "postalCode": "73021",
                        "countryCode": "USA"
                    }
                ],
                "firstName": "Scoobert",
                "customData": {},
                "middleName": "",
                "phoneNumbers": [
                    {
                        "isMobile": true,
                        "isPrimary": true,
                        "phoneNumber": "+17352730021",
                        "hasCellPhoneConsent": true
                    }
                ],
                "activePrivacy": true,
                "ecorrAccepted": true,
                "activeMilitary": false,
                "borrowerNumber": "",
                "emailAddresses": [
                    {
                        "isPrimary": true,
                        "emailAddress": "example@nelnet.net"
                    }
                ],
                "externalReferenceId": "7373u10"
            },
            "loan": {
                "term": 20,
                "amount": 5000,
                "margin": 0,
                "status": "repayment",
                "isActive": true,
                "rateType": "Fixed",
                "customData": {},
                "loanNumber": "",
                "interestRate": 4.5,
                "paymentAmount": 50,
                "disbursementDate": "2015-08-01",
                "firstPaymentDate": "2020-03-01",
                "externalReferenceId": "7373u10",
                "paymentScheduleType": "fixed payment",
                "investors": [
                    {
                        "investorId": "string"
                    }
                ]
            },
            "autoDebit": null,
            "bankProfile": null,
            "cellPhoneConsent": [
                {
                    "isMobile": true,
                    "hasConsent": true,
                    "phoneNumber": "+17352730021"
                }
            ],
            "validation": {
                "loan": "Skipped",
                "wallet": "Skipped",
                "borrower": "Skipped",
                "autoDebit": "Skipped",
                "completed": "Skipped",
                "bankProfile": "Skipped",
                "cellPhoneConsent": "Skipped"
            },
            "steps": {
                "loan": "Success",
                "wallet": "Skipped",
                "borrower": "Success",
                "callBack": "Skipped",
                "autoDebit": "Skipped",
                "completed": "Success",
                "bankProfile": "Skipped",
                "cellPhoneConsent": "Success"
            },
            "ids": {
                "loanId": "45ebf300-eb5e-4fdc-91b3-c08b1d1e3374",
                "walletId": null,
                "borrowerId": "61e95938-fcf6-4ecd-b081-912d719b6750",
                "autoDebitId": null,
                "bankProfileId": null,
                "cellPhoneConsentIds": [
                    "45ac1fe1-eb97-4786-b08c-1967990d2de8"
                ]
            },
            "errors": [],
            "errorDate": null,
                        "createdBy": {
                "aud": "string",
                "exp": 1111111111,
                "iat": 1111111111,
                "iss": "string",
                "sub": "string",
                "email": "string",
                "groups": [
                    "processor"
                ],
                "region": "string",
                "eventId": "string",
                "lenders": [
                    "string",
                    "string"
                ],
                "authTime": 1111111111,
                "clientId": "2",
                "tenantId": "314",
                "tokenUse": "id",
                "userName": "string",
                "borrowerId": null,
                "servicerId": "2",
                "userPoolId": "us-west-2_WHSE88shs",
                "phoneNumber": "string",
                "poolClientId": "string",
                "emailVerified": true,
                "phoneNumberVerified": true
            },
            "updatedBy": {
                "aud": "string",
                "exp": 1111111111,
                "iat": 1111111111,
                "iss": "string",
                "sub": "string",
                "email": "string",
                "groups": [
                    "processor"
                ],
                "region": "string",
                "eventId": "string",
                "lenders": [
                    "string",
                    "string"
                ],
                "authTime": 1111111111,
                "clientId": "2",
                "tenantId": "314",
                "tokenUse": "id",
                "userName": "string",
                "borrowerId": null,
                "servicerId": "2",
                "userPoolId": "us-west-2_WHSE88shs",
                "phoneNumber": "string",
                "poolClientId": "string",
                "emailVerified": true,
                "phoneNumberVerified": true
            },
            "updatedDate": "2020-08-03T19:49:43.681Z",
            "isLoanCancelled": null,
            "loanCancelledReason": null
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 1,
        "links": {
            "first": "/bundle?offset=0&limit=1",
            "last": "/bundle?offset=1481&limit=1",
            "next": "/bundle?offset=1&limit=1"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns an onboarding request.**

### HTTP Request

`GET https://api.nelnet.io/onboardingapi/onboard/bundles`

All of the following query parameters are optional in the request.

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
onboardingid | no | string | The onboarding ID created by a (successful) onboarding via call to the POST /onboard/bundle endpoint.
loanProgramid | no | string | The identifier for the loan program.
itemid | no | string | The identifier for the onboarding item.
batchid | no | string | The identifier for the onboarding batch.
offset | no | number | Use to set which record to start with in the response. Default value: 0
limit | no | number | Use to limit the number of onboarding records returned in the response. Default value: 20

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
offset | number | The starting record in the return - the offset between the records returned and list of total records.
limit | number | The number of records per page.
links | object | Information about the pagination and links in the response.
first | string | A link to the first page of records returned.
last | string | A link to the last page of records returned.
previous | string | A link to the previous page in the list of records returned.
next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following is contained within `data`.
onboardingId | string | A system-generated identifier for the onboarding request.
tenantId | string | Identifier for the tenant.
servicerId | string | Identifier for the servicer.
loanProgramId | UUID (string) | The identifier for the loan program.
lenderId | UUID (string) | The identifier for the lender.
itemId | string | The identifier for the onboarding item. This can be queried once posted.
batchId | string | The identifier for the onboarding batch. This can be queried once posted.
callBackURL | string | Optional callback URL to point an event response to an external source.
|||
borrower | object | The borrower record is required if onboarding a new borrower and a new loan.
borrower.borrowerId | UUID (string) | To add a new loan to an existing borrower, enter the borrower ID for that borrower.
borrower.firstName | string | Required for a new borrower. The borrower's first name.
borrower.middleName | string | The borrower's middle name (if applicable).
borrower.lastName | string | Required for a new borrower. The borrower's last name.
borrower.suffix | string | The suffix (*Jr.*, *III*, etc.) within the borrower's name (if applicable).
borrower.ssn | string | The borrower's Social Security number, in the 9-digit format without dashes (*111223333*).
borrower.dob | string | The borrower's date of birth, in the YYYY-MM-DD format.
borrower.addresses | array | Array of addresses (at least one address is required). See the [borrower addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.phoneNumbers | array | Array of phone numbers (at least one phone number is required). See the [borrower phone numbers table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.emailAddresses | array | Array of email addresses. See the [borrower email addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.customData | object | Set up for future use.
borrower.activeMilitary | boolean | Indicates whether the borrower is set to receive SCRA benefits.
borrower.activePrivacy | boolean | Indicates whether the borrower's privacy flag is set to true or false.
borrower.externalReferenceId | string | Unique identifier for the borrower record — can be set to anything, but must be unique.
borrower.ecorrAccepted | boolean | Defaults to *true*. Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
|||
loan | object | The loan object is required for all calls to this endpoint.
loan.term | number | The loan's term, in billing cycles. For fixed-payment (rather than fixed-term) loans, `term` may be changed via the payment-schedule calculation that occurs as part of the onboarding process.
loan.amount | number | The loan total amount, as of today, in dollars.
loan.interestRate | number | The loan's current interest rate, as a percentage.
loan.margin | number | The loan's margin amount. For fixed-term loans, this should be set to 0.
loan.rateType | enum |Whether the loan's rate changes over time (variable) or is constant (fixed). Defaults to *fixed*. Options: *fixed*, *variable*.
loan.paymentScheduleType | enum | Whether the loan's payment schedule is determined by a fixed payment amount or a fixed term (resulting in variable payment amounts over the life of the loan). Options: *fixed term*, *fixed payment*. Defaults to *fixed term*. **Note**: If using *fixed payment*, `paymentAmount` is required and must be numeric and greater than 0.
loan.disbursementDate | string | The date on which the loan funds were disbursed to the borrower, in the YYYY-MM-DD format. Must be today or any date before today (can't be in the future).
loan.firstPaymentDate | string | The borrower's first payment due date, in the YYYY-MM-DD format. Must be after the `disbursementDate` **and** after today (can't be in the past).
loan.originationFee | number | The amount of the disbursement charged to the borrower (in addition to the loan amount) for the origination of the loan.
loan.paymentAmount | number | The minimum required monthly payment amount, at the time the loan is being onboarded.
loan.status | enum | The current status of the loan. Defaults to *repayment*. Options: *repayment, paid in full, charge off, write off, forbearance, default, fraud, rejected*.
loan.externalReferenceId | string | Unique identifier for the loan record — can be set to anything, but must be unique.
loan.customData | object | Placeholder for any additional data to be stored with the record.
loan.isActive | boolean | Indicates whether the loan is active. Defaults to *true*.
loan.investors | object | Information about investors.
loan.investorId | string | The identifier for the investor associated with the loan.
|||
autoDebit | object | If used, the method also creates a bank profile that's populated with the auto debit information.
autoDebit.routingNumber | string | The 9-digit routing number for the account that's set up to be automatically debited for payments on this loan.
autoDebit.accountNumber | string | The account number for the account that's set up to be automatically debited for payments on this loan. Can be between 4 and 17 digits long.
autoDebit.accountType | enum | Account type for the account used by auto debit. Options: *Checking*, *Saving*.
autoDebit. accountHolderFirstName | string | The account holder's first name.
autoDebit. accountHolderLastName | string | The account holder's last name.
autoDebit.terms | object | The terms and conditions for auto debit agreed to by the borrower.
autoDebit.terms.type | enum | The type of terms and conditions content included in the auto debit signup. Options: *HTML, ID, Text, URL.*
autoDebit.terms.content | string | The content of the terms and conditions disclosure.
autoDebit.isActive | boolean | Set to *true* to onboard a loan with an active auto debit profile. Set to *false* to onboard a loan with auto debit information that not currently in use - the result will be that the borrower has an auto debit profile associated, but that auto ebit will not be used to collect payment unless it's activated.
bankProfile | object | Contains bank-profile information.
bankProfile.bankProfileName | string | The customer-borrower can set up multiple bank profiles for use in making payments, and sets a unique name for each bank profile.
bankProfile.routingNumber | string | The 9-digit routing number for the account associated with the bank profile. 
bankProfile.accountNumber | string | The account number for the account associated with the bank profile. Can be between 4 and 17 digits long.
bankProfile.accountType | enum | Account type for the bank profile account. Options: *Checking*, *Saving*.
bankProfile. accountHolderFirstName | string | The account holder's first name.
bankProfile. accountHolderLastName | string | The account holder's last name.
cellPhoneConsent | array | Information about cell phone consent collection.
cellPhoneConsent. phoneNumber | string | Borrower's E.164-formatted cell phone number.
cellPhoneConsent. hasConsent | boolean | Indicates whether the borrower has opted in for contact via cell phone.
cellPhoneConsent. isMobile | boolean | Indicates whether the phone number provided is a cell phone/number for a mobile phone.
cellPhoneConsent.createdBy | string | The Velocity user account used to create the cell phone consent flag.
validation | object | Validation collection.
validation.autoDebit | string | Answers the question: Did the auto debit process validate? Options: *Pending, Skipped, Success, Failure*.
validation.bankProfile | string | Answers the question: Did the bank profile process validate? Options: *Pending, Skipped, Success, Failure*.
validation.borrower | string |  Answers the question: Did the borrower process validate? Options: *Pending, Skipped, Success, Failure*.
validation.cellPhoneConsent | string |  Answers the question: Did the cell phone consent process validate? Options: *Pending, Skipped, Success, Failure*.
validation.loan | string |  Answers the question: Did the loan process validate? Options: *Pending, Skipped, Success, Failure*.
validation.completed | string |  Answers the question: Did the onboarding validate? Options: *Pending, Skipped, Success, Failure*.
steps | object | Step collection — used in validation/processing.
steps.autoDebit | string | Answers the question: Did the auto debit addition complete? Options: *Pending, Skipped, Success, Failure*.
steps.bankProfile | string | Answers the question: Did the bank profile addition complete? (Bank profiles are automatically created if auto debit information is added for a borrower.) Options: *Pending, Skipped, Success, Failure*.
steps.borrower | string | Answers the question: Did the borrower addition complete? Options: *Pending, Skipped, Success, Failure*. (A borrower may not be added but the onboard is still successful, like when added a loan to an existing borrower record.)
steps.cellPhoneConsent | string | Answers the question: Did the addition of a borrower's cell phone data complete? Options: *Pending, Skipped, Success, Failure*
steps.loan | string | Answers the question: Did the additional of the loan complete? Options: *Pending, Skipped, Success, Failure*.
steps.callBack | |
steps.wallet | |
steps.completed | string | Answers the question: Did the onboarding process complete? Options: *Pending, Skipped, Success, Failure*.
ids | object | ID collection.
ids.loanId | string | ID of the loan that was created.
ids.borrowerId | string | ID of the borrower that was created or added to (if onboarding a loan to an existing user).
ids.autoDebitId | string | ID of the autodebit configuration that was created.
ids.bankProfileId | string | ID of the bank profile that was created.
ids.cellPhoneConsentIds | array strings | IDs of the cell phone consent records that was created
errors | array | Collection of errors potentially returned.
errorDate | string | Date of the last error.
createdBy | string | User who created the onboarding request.
createdDate | string | Date the onboarding record was created.
updatedBy | string | User who updated the onboarding request.
updatedDate | string | Date the onboarding record was updated.
isLoanCancelled | |
loanCancelledReason | string |