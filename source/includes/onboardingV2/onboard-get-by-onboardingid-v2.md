<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->
## Get Specific onboarding Results (GET by OnboardingID)

### GET /onboarding/bundles/{onboardingid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/lenderapi/onboardingapi-v2/onboarding/bundles/e9b10808-4f6a-4cbd-8b4d-ea0e6f87e12f \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache' \
  -H 'servicerid: 2' \
  -H 'tenantid: 314'
```

```csharp
var client = new RestClient("https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/e9b10808-4f6a-4cbd-8b4d-ea0e6f87e12f");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddHeader("servicerid", "2");
request.AddHeader("tenantid", "314");
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
xhr.open("GET", "https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/e9b10808-4f6a-4cbd-8b4d-ea0e6f87e12f");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");
xhr.send(data);
```

```python
import http.client
conn = http.client.HTTPConnection("api,nelnet,io")
payload = ""
headers = {
    'tenantid': "314",
    'servicerid': "2",
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }
conn.request("GET", "/onboardingapi-v2/onboarding/bundles/e9b10808-4f6a-4cbd-8b4d-ea0e6f87e12f", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
  "loan": {
    "ids": [
      {
        "loanId": "string",
        "loanNumber": "string",
        "createdDate": "string"
      }
    ],
    "errors": [
      null
    ],
    "status": "Success",
    "payloads": [],
    "requests": [
      {
        "term": 0,
        "margin": 0,
        "status": "repayment",
        "isActive": true,
        "rateType": "Fixed",
        "borrowers": [
          {
            "borrowerId": "string",
            "borrowerType": "string",
            "borrowerFullName": "string"
          },
          {
            "borrowerId": "string",
            "borrowerType": "string",
            "borrowerFullName": "string"
          }
        ],
        "investors": [
          {
            "investorId": "string"
          }
        ],
        "loanPeriods": [
          {
            "fixedAmount": {
              "startDate": "string",
              "reduceTerm": true,
              "paymentAmount": 0,
              "loanPeriodTags": [
                "Leaky Couldron"
              ],
              "firstPaymentDate": "string",
              "paymentFrequency": "monthly",
              "capInterestAtStart": true
            }
          }
        ],
        "interestRate": 0,
        "disbursements": [
          {
            "amount": 0,
            "originationFee": 0,
            "disbursementDate": "string",
            "externalReferenceId": "string"
          }
        ],
        "loanProgramId": "string",
        "externalReferenceId": "string"
      }
    ],
    "returnIdName": "string"
  },
  "student": {
    "ids": [],
    "errors": [],
    "status": "Skipped",
    "payloads": [],
    "requests": [],
    "returnIdName": "string"
  },
  "borrowers": {
    "ids": [
      {
        "borrowerId": "string",
        "createdDate": "string",
        "borrowerNumber": "string"
      },
      {
        "borrowerId": "string",
        "createdDate": "string",
        "borrowerNumber": "string"
      }
    ],
    "errors": [
      null,
      null
    ],
    "status": "string",
    "payloads": [],
    "requests": [
      {
        "dob": "string",
        "ssn": "string",
        "lastName": "string",
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
        "firstName": "string",
        "middleName": "string",
        "borrowerType": "string",
        "phoneNumbers": [
          {
            "type": "string",
            "isMobile": true,
            "isPrimary": true,
            "phoneNumber": "string",
            "hasCellPhoneConsent": true
          }
        ],
        "activePrivacy": true,
        "ecorrAccepted": true,
        "activeMilitary": false,
        "emailAddresses": [
          {
            "isPrimary": true,
            "emailAddress": "string"
          }
        ],
        "externalReferenceId": "string",
        "communicationPreferences": []
      },
      {
        "dob": "string",
        "ssn": "string",
        "lastName": "string",
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
        "firstName": "string",
        "middleName": "string",
        "borrowerType": "string",
        "phoneNumbers": [
          {
            "type": "string",
            "isMobile": true,
            "isPrimary": true,
            "phoneNumber": "string",
            "hasCellPhoneConsent": true
          }
        ],
        "activePrivacy": true,
        "ecorrAccepted": true,
        "activeMilitary": false,
        "emailAddresses": [
          {
            "isPrimary": true,
            "emailAddress": "string"
          }
        ],
        "externalReferenceId": "string",
        "communicationPreferences": []
      }
    ],
    "returnIdName": "string"
  },
  "autoDebits": {
    "ids": [
      [
        {
          "autoDebitId": "string",
          "createdDate": "string"
        }
      ],
      []
    ],
    "errors": [
      null,
      [
        {
          "timestamp": "string",
          "apiResponse": {
            "body": {
              "info": "string",
              "description": "string"
            },
            "name": "string",
            "statusCode": 404
          }
        }
      ]
    ],
    "status": "string",
    "payloads": [],
    "requests": [
      [
        {
          "terms": {
            "type": "string",
            "content": "string"
          },
          "loanId": "string",
          "isActive": true,
          "borrowerId": "string",
          "accountType": "string",
          "isAutoDebit": true,
          "accountNumber": "string",
          "routingNumber": "string",
          "accountHolderLastName": "string",
          "accountHolderFirstName": "string"
        }
      ],
      [
        {
          "terms": {
            "type": "string",
            "content": "string"
          },
          "loanId": "string",
          "isActive": true,
          "borrowerId": "string",
          "accountType": "Checking",
          "isAutoDebit": true,
          "accountNumber": "string",
          "routingNumber": "string",
          "accountHolderLastName": "string",
          "accountHolderFirstName": "string"
        }
      ]
    ],
    "returnIdName": "string"
  },
  "bankProfiles": {
    "ids": [
      [
        {
          "createdDate": "string",
          "bankProfileId": "string"
        }
      ],
      [
        {
          "createdDate": "string",
          "bankProfileId": "string"
        }
      ]
    ],
    "errors": [],
    "status": "string",
    "payloads": [
      [
        {
          "autoDebit": {
            "accountType": "Checking",
            "isAutoDebit": true,
            "accountNumber": "string",
            "routingNumber": "string",
            "accountHolderLastName": "string",
            "accountHolderFirstName": "string"
          }
        }
      ],
      [
        {
          "autoDebit": {
            "accountType": "Checking",
            "isAutoDebit": true,
            "accountNumber": "string",
            "routingNumber": "string",
            "accountHolderLastName": "string",
            "accountHolderFirstName": "string"
          }
        }
      ]
    ],
    "requests": [
      [
        {
          "borrowerId": "string",
          "accountType": "Checking",
          "isAutoDebit": true,
          "accountNumber": "string",
          "routingNumber": "string",
          "bankProfileName": "string",
          "accountHolderLastName": "string",
          "accountHolderFirstName": "string"
        }
      ],
      [
        {
          "borrowerId": "string",
          "accountType": "Checking",
          "isAutoDebit": true,
          "accountNumber": "string",
          "routingNumber": "string",
          "bankProfileName": "string",
          "accountHolderLastName": "string",
          "accountHolderFirstName": "string"
        }
      ]
    ],
    "returnIdName": "string"
  }
}
```

<!-- LEFT: documentation -->

**Returns an onboarding request, showing the results of a call to the onboarding endpoint.**

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`GET https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/{onboardingid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
onboardingid | Yes | UUID (string) | The onboarding ID created by a (successful) call to the POST /onboarding/bundles endpoint.


### HTTP Response
The response payload `ResponseBodyBundle` contains the following.

Field Name | Type   | Description
---------- | ------ | -------
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
borrowers | object | The borrower object.
borrowers.borrowerId | UUID (string) | A system-generated borrower identifier for the onboarding request.
borrowers.borrowerType | string | A designation for borrower categories.
borrowers.firstName | string | The borrower's first name.
borrowers.middleName | string | The borrower's middle name (if applicable).
borrowers.lastName | string | The borrower's last name.
borrowers.suffix | string | The suffix (*Jr.*, *III*, etc.) within the borrower's name (if applicable).
borrowers.ssn | string | The borrower's Social Security number, in the 9-digit format without dashes (*111223333*).
borrowers.dob | string | The borrower's date of birth, in the YYYY-MM-DD format.
borrowers.addresses | array | Array of addresses (at least one address is required).
borrowers.phoneNumbers | array | Array of phone numbers (at least one phone number is required).
borrowers.emailAddresses | array | Array of email addresses.
borrowers.customData | object | Set up for future use.
borrowers.<br />activeMilitary | boolean | Indicates whether the borrower is set to receive SCRA benefits.
borrowers.<br />activePrivacy | boolean | Indicates whether the borrower's privacy flag is set to true or false.
borrowers.<br />externalReferenceId | string | Unique identifier for the borrower record added via the POST onboarding method.
borrowers.ecorrAccepted | boolean | Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
borrowers.walletId | string | The identifier for the wallet associated with the borrower.
borrowers.bankProfiles | object | Information about any bank profiles saved for the borrower.
borrowers.bankProfiles.<br />bankProfileId | string| ID value associated with the borrower.
borrowers.bankProfiles.<br />bankProfileName | string | Friendly name values for the bank profile associated with the borrower.
borrowers.bankProfiles.<br />routingNumber | string | The bank routing number associated with the bank profile.
borrowers.bankProfiles.<br />accountNumber | string | The account number associated with the bank profile.
borrowers.bankProfiles.<br />accountType | string (enum) | The type of bank account associated with the account number within the bank profile. Options: *Chcking*, *Savings*.
borrowers.bankProfiles.<br />acountHolderFirstName | string | The first name of the account holder for the bank profile.
borrowers.bankProfiles.<br />accountHolderLastName | string | the last name of the account for the bank profile.
borrowers.bankProfiles.<br />isAutoDebit | boolean | Whether the account is set up for auto debit.
borrowers.autoDebit | object | Information about auto debit settings.
borrowers.autoDebit.<br />autoDebitID | string | ID of the autodebit configuration.
borrowers.autoDebit.<br />terms | object | Information about auto debit terms of use.
borrowers.autoDebit.<br />terms.type | string (enum) | The term type for auto debit. Options *HTML*, *ID*, *Text*, *URL*.
borrowers.autoDebit.<br />terms.content | string | The content of the auto debit terms.
borrowers.autoDebit.<br />isActive | boolean | Whether auto debit is active for the borrower.
borrowers.references | object | Information about reference(s) for the borrower.
borrowers.references.<br />relationId | string | The ID for the borrower relationship
borrowers.references.<br />firstName | string | The reference's first name.
borrowers.references.<br />middleName | string | The reference's middle name.
borrowers.references.<br />lastName | string | The reference's last name.
borrowers.references.<br />street1 | string | The reference's address street line 1.
borrowers.references.<br />street2 | string | The reference's address street line 2.
borrower.references.<br />city | string | The city for the reference's address.
borrowers.references.<br />state | string | The state for the reference's address.
borrowers.references.<br />postalCode | string | The postal code for the reference's address.
borrowers.references.<br />countryCode | string | The country code for the reference's address.
borrowers.references.<br />phoneNumber | string | The phone number for the reference.
borrowers.references.<br />emailAddress | string | The email address for the reference.
|||
loan | object | The loan object.
loan.term | integer | The loan's term, in billing cycles. For fixed-payment (rather than fixed-term) loans, `term` may be changed via the payment-schedule calculation that occurs as part of the onboarding process.
loan.interestRate | number | The loan's current interest rate, as a percentage.
loan.margin | number | The loan's margin amount. For fixed-term loans, this should be set to 0.
loan.rateType | string (enum) |  The rate type for the loan. Defaults to *fixed*. Options: Fixed, variable.
loan.externalReferenceId | string | Unique identifier for the loan record — can be set to anything, but must be unique.
loan.loanNumber | string | The loan number.
loan.customData | |
loan.investors | object | Information about investors.
loan.invenstors.investorId | string | The identifier for the investor associated with the loan.
loan.disbursements. | object | Information about disbursements associated with the loan.
loan.disbursements.<br />externalReferenceId | string | An optional external reference identifier for the disbursement.
loan.disbursements.<br />disbursementDate  | string | The disbursement date.
loan.disbursements.<br />amount | number | The disbursement amount.
loan.disbursements.<br />originationFee | number | The amount of the disbursement charged to the borrower (in addition to the loan amount) for the origination of the loan.
loan.loanPeriods | object | Information about loan periods.
loan.loanPeriods.<br />fixedAmount | object | Information about fixed amount loan periods.
loan.loanPeriods.<br />fixedAmount.paymentAmount | number | The minimum required monthly payment amount, at the time the loan is being onboarded.
loan.loanPeriods.<br />fixedAmount.firstPaymentDate | string | The date that the first payment is due.
loan.loanPeriods.<br />fixedAmount.paymentFrequency | string | The frequency for the loan. Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />fixedAmount.capInterestAtStart | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriods.<br />fixedAmount.startDate | string | The starting date for the loan period.
loan.loanPeriods.<br />fixedAmount.reduceTerm |	boolean | 
loan.loanPeriods.<br />fixedAmount.loanPeriodTags	| string |
loan.loanPeriods.<br />fixedAmount.reportingStatus | string |
loan.loanPeriods.<br />fixedAmount.loanStatus	|string (enum) | Options: *repayment*, *deferred*
loan.loanPeriods.deferment | object |
loan.loanPeriods.<br />deferment.<br />capInterestAtStart | boolean |
loan.loanPeriods.<br />deferment.startDate | string |
loan.loanPeriods.<br />deferment.<br />reduceTerm | boolean |
loan.loanPeriods.<br />deferment.<br />loanPeriodTags | string |
loan.loanPeriods.<br />deferment.<br />reportingStatus | string |
loan.loanPeriods.<br />deferment.<br />loanStatus | string (enum) | Options *repayment*, *deferred*
loan.loanPeriods.<br />interestOnly | object |
loan.loanPeriods.<br />interestOnly.<br />firstPaymentDate | string |
loan.loanPeriods.<br />interestOnly.<br />paymentFrequency | string (enum) | Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />interestOnly.<br />capInterestAtStart | boolean |
loan.loanPeriods.<br />interestOnly.<br />startDate | string |
loan.loanPeriods.<br />interestOnly.<br />reductTerm |string |
loan.loanPeriods.<br />interestOnly.loanStatus | string (enum) | Options *repayment*, *deferred*
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest | object |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />firstPaymentDate | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />paymentFrequency | string (enum) | Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />capInterestAtStart | boolean |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />startDate | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />reductTerm |string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />loanPeriodTags | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.<br />loanStatus	|string (enum) | Options: *repayment*, *deferred*
|||
student | object |
student.enrollmentId | string |
student.isBorrower | boolean |
student.firstName | string |
student.middleName | string |
student.lastName | string |
student.ssn | string |
student.externalReferenceId | string |
student.schoolName | string |
student.schoolCode | string |
student.programCode |string |
student.status | string (enum) | Options: *Full Time*, *Three Quarter Time*, *Half Time*, *Less than Half Time*, *Leave of Absence*, *Graduated*, *Withdrawn*, *Deceased*, *Never Enrolled*.
student.graduationDate | string | Date of graduation.
|||
steps | object | Step collection — used in validation/processing.
steps.borrowers | object |
steps.borrowers.ids | |
steps.borrowers.returnIdName | string |
steps.borrowers.errors | |
steps.borrowers.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.borrowers.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.borrowers.payloads | |
steps.borrowers.requests | |
steps.loan | object |
steps.loan.ids | |
steps.loan.returnIdName | string |
steps.loan.errors | |
steps.loan.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.loan.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.loan.payloads | |
steps.loan.requests | |
steps.bankProfile | object |
steps.bankProfile.ids | |
steps.bankProfile.returnIdName | string |
steps.bankProfile.errors | |
steps.bankProfile.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.bankProfile.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.bankProfile.payloads | |
steps.bankProfile.requests | |
steps.autoDebits | object |
steps.autoDebits.ids | |
steps.autoDebits.returnIdName | string |
steps.autoDebits.errors | |
steps.autoDebits.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.autoDebits.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.autoDebits.payloads | |
steps.autoDebits.requests | |
steps.cellPhoneConsent | object |
steps.cellPhoneConsent.ids | |
steps.cellPhoneConsent.returnIdName | string |
steps.cellPhoneConsent.errors | |
steps.cellPhoneConsent.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.cellPhoneConsent.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.cellPhoneConsent.payloads | |
steps.cellPhoneConsent.requests | |
steps.wallets | object |
steps.wallets.ids | |
steps.wallets.returnIdName | string |
steps.wallets.errors | |
steps.wallets.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.wallets.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.wallets.payloads | |
steps.wallets.requests | |
steps.references | object |
steps.references.ids | |
steps.references.returnIdName | string |
steps.references.errors | |
steps.references.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.references.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.references.payloads | |
steps.references.requests | |
steps.student | object |
steps.student.ids | |
steps.student.returnIdName | string |
steps.student.errors | |
steps.student.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.student.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.student.payloads | |
steps.student.requests | |
steps.callBack | object |
steps.callBack.ids | |
steps.callBack.returnIdName | string |
steps.callBack.errors | |
steps.callBack.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.callBack.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.callBack.payloads | |
steps.callBack.requests | |
steps.completed | object |
steps.completed.ids | |
steps.completed.returnIdName | string |
steps.completed.errors | |
steps.completed.status | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.completed.validationStatus | string (enum) | Options: *Pending*, *Failure*, *Skipped*, *Success*.
steps.completed.payloads | |
steps.completed.requests | |
|||
createdBy | string | User who created the onboarding request.
createdDate | string | Date the onboarding record was created.
updatedBy | string | User who updated the onboarding request.
updatedDate | string | Date the onboarding record was updated.
isLoanCancelled | string | boolean | flag for whether the loan is canceled.
loanCancelledReason | string | the reasons entered for the cancelation.
