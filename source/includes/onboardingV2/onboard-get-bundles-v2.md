<!--You can make edits and remove comments if desired, but be sure to check your work as some formatting changes in this source file can affect how the end product builds. -->
<!--Endpoint introduction -->
## Get Bundles of Onboarding-V2 Results (GET by Onboarding-V2 Bundle)

### GET /onboarding/bundles

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

**Returns onboarding request bundles.**

<!-- Use <aside class="notice"></aside> to add notices if needed -->

### HTTP Request

`GET https://api.nelnet.io/onboardingapi-v2/onboarding/bundles`

All of the following query parameters are optional in the request.

Parameter | Required | Type   | Description
--------- | -------- | ------ | -----------
loanprogramID | no | string | The identifier for the loan program.
itemid | no | string | The identifier for the onboarding item.
batchid | no | string | The identifier for the onboarding batch.
offset | no | number | Use to set which record to start with in the response. Default value: 0
limit | no| number | Use to limit the number of onboarding records returned in the response. Default value: 20


### HTTP Response

Field Name | Type   | Description
---------- | ------ | -----------
paging | object | Information about the paging of the results returned, within the total results available.
rows | number | The number of rows per page.
pages | number | The number of pages.
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
borrower | object | The borrower record is required if onboarding a new borrower and a new loan.
borrower.borrowerId | string | To add a new loan to an existing borrower, enter the borrower ID for that borrower.
borrower.firstName | string | Required for a new borrower. The borrower's first name.
borrower.middleName | string | The borrower's middle name (if applicable).
borrower.lastName | string | Required for a new borrower. The borrower's last name.
borrower.suffix | string | The suffix (Jr., III, etc.) within the borrower's name (if applicable).
borrower.ssn | string | The borrower's Social Security number, in the 9-digit format without dashes (111223333).
borrower.dob | string | The borrower's date of birth, in the YYYY-MM-DD format.
borrower.addresses | array | Array of addresses (at least one address is required). See the [borrower addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.phoneNumbers | array | Array of phone numbers (at least one phone number is required). See the [borrower phone numbers table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.emailAddresses | array | Array of email addresses. See the [borrower email addresses table](https://docs.nelnet.io/#borrower-information-arrays) for full details.
borrower.customData | object | Set up for future use.
borrower.activeMilitary | boolean | Indicates whether the borrower is set to receive SCRA benefits.
borrower.activePrivacy | boolean | Indicates whether the borrower's privacy flag is set to true or false.
borrower.externalReferenceId	| string | Unique identifier for the borrower record — can be set to anything, but must be unique.
borrower.borrowerNumber | string | The borrower number.
borrower.ecorrAccepted | boolean | Defaults to *true*. Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
borrower.walletId | string | The identifier for the wallet associated with the borrower.
borrower.bankProfiles | object | Information about any bank profiles saved for the borrower.
borrower.bankProfiles.<br />bankProfileId | string | ID of the bank profile associated with the borrower.
borrower.bankProfiles.<br />bankProfileName | string | Friendly name values for the bank profile associated with the borrower.
borrower.bankProfiles.<br />routingNumber | string | The bank routing number associated with the bank profile.
borrower.bankProfiles.<br />accountNumber | string | The account number associated with the bank profile.
borrower.bankProfiles.<br />accountType | string(enum) | The type of bank account associated with the account number within the bank profile. Options Checking, Savings.
borrower.bankProfiles.<br />accountHolderFirstName | string | The first name of the account holder for the bank profile.
borrower.bankProfiles.<br />accountHolderLastName | string | The last name of the account holder for the bank profile.
borrower.bankProfiles.<br />isAutoDebit | boolean | Whether the account is set up for auto debit.
borrower.autoDebit | object | Information about auto debit settings.
borrower.autoDebit.<br />autoDebitId | string | ID of the autodebit configuration.
borrower.autoDebit.<br />autoDebitTerms | object | Information about auto debit terms of use.
borrower.autoDebit.<br />autoDebitTerms.type | string (enum) | The term type for auto debit. Options HTML, ID, Text, URL.
borrower.autoDebit.<br />autoDebitTerms.content | string | The content of the auto debit terms.
borrower.autoDebit.<br />isActive | boolean | Whether auto debit is active for the borrower.
borrower.references | object | Information about reference(s) for the borrower.
borrower.references.<br />relationId | string | The ID for the borrower relationship
borrower.references.<br />fistName | string | The reference's first name.
borrower.references.<br />middleName | string | The reference's middle name.
borrower.references.<br />lastName | string | The reference's last name.
borrower.references.<br />street1 | string | The reference's address street line 1.
borrower.references.<br />street2 | string | The reference's address street line 2.
borrower.references.<br />city | string | The city for the reference's address.
borrower.references.<br />state | string | The state for the reference's address.
borrower.references.<br />postalCode | string | The postal code for the reference's address.
borrower.references.<br />countryCode | string | The country code for the reference's address.
borrower.references.<br />phoneNumber | string | The phone number for the reference.
borrower.references.<br />emailAddress | string | The phone number for the reference.
|||
loan | object | The loan object is required for all calls to this endpoint.
loan.loanId | string | Loan identifier.
loan.term | number | The loan's term, in billing cycles. For fixed-payment (rather than fixed-term) loans, `term` may be changed via the payment-schedule calculation that occurs as part of the onboarding process.
loan.interestRate | number | The loan's current interest rate, as a percentage.
loan.margin | number | The loan's margin amount. For fixed-term loans, this should be set to 0.
loan.rateType | string (enum) | Whether the loan's rate changes over time (variable) or is constant (fixed). Defaults to *fixed*. Options: *fixed*, *variable*.
loan.externalReferenceId | string | Unique identifier for the loan record — can be set to anything, but must be unique.
loan.loanNumber | string | The loan number.
loan.customData | object | Placeholder for any additional data to be stored with the record.
loan.investors | object | Information about investors.
loan.investors.investorId | string | The identifier for the investor associated with the loan.
loan.disbursements | object | Information about disbursements associated with the loan.
loan.disbursements.externalReferenceId | string | An optional external reference identifier for the disbursement.
loan.disbursements.disbursementDate | string | The disbursement date.
loan.disbursements.amount | number | The disbursement amount.
loan.disbursements.originationFee | number | The amount of the disbursement charged to the borrower (in addition to the loan amount) for the origination of the loan.
loan.loanPeriods | object | Information about loan periods.
loan.loanPeriods.<br />fixedAmount | object | Information about fixed amount loan periods.
loan.loanPeriods.<br />fixedAmount.paymentAmount | number | The minimum required monthly payment amount, at the time the loan is being onboarded.
loan.loanPeriods.<br />fixedAmount.firstPaymentDate | string | The date that the first payment is due.
loan.loanPeriods.<br />fixedAmount.paymentFrequency | string (enum) | The frequency at which payments are required. Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />fixedAmount.capInterestAtStart | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriods.<br />fixedAmount.startDate | string | The starting date for the loan period.
loan.loanPeriods.<br />fixedAmount.reduceTerm | boolean | Whether the payment reduces the term of the loan.
loan.loanPeriods.<br />fixedAmount.loanPeriodTags | string | The loan period tags.
loan.loanPeriods.<br />fixedAmount.reportingStatus | string | The reporting status.
loan.loanPeriods.<br />fixedAmount.loanStatus | string (enum) | The status of the loan. Options *repayment*, *deferred*.
loan.loanPeriods.<br />loanPeriodDeferment | object | Information about deferment loan periods.
loan.loanPeriods.<br />loanPeriodDeferment.capInterestAtStart | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriods.<br />loanPeriodDeferment.startDate | string | The loan period start date.
loan.loanPeriods.<br />loanPeriodDeferment.reduceTerm | boolean | Whether the loan period reduces the term.
loan.loanPeriods.<br />loanPeriodDeferment.loanPeriodTags | string | The loan period tags.
loan.loanPeriods.<br />loanPeriodDeferment.reportingStatus |string | The reporting status.
loan.loanPeriods.<br />loanPeriodDeferment.loanStatus | string (enum) | The loan status. Options *repayment*, *deferred*
loan.loanPeriods.<br />loanPeriodInterestOnly | object | Information about interest only loan periods.
loan.loanPeriods.<br />loanPeriodInterestOnly.firstPaymentDate | string | 
loan.loanPeriods.<br />loanPeriodInterestOnly.paymentFrequency | string (enum) | Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />loanPeriodInterestOnly.capInterestAtStart | boolean |
loan.loanPeriods.<br />loanPeriodInterestOnly.startDate | string |
loan.loanPeriods.<br />loanPeriodInterestOnly.reduceTerm | boolean |
loan.loanPeriods.<br />loanPeriodInterestOnly.loanPeriodTags | string |
loan.loanPeriods.<br />loanPeriodInterestOnly.reportingStatus | string |
loan.loanPeriods.<br />loanPeriodInterestOnly.loanStatus | string (enum) | Options *repayment*, *deferred*
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest | object |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.firstPaymentDate | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.paymentFrequency | string (enum) | Options *weekly*, *bi-weekly*, *monthly*, *quarterly*.
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.capInterestAtStart | boolean |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.startDate | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.reduceTerm | boolean |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.loanPeriodTags | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.reportingStatus | string |
loan.loanPeriods.<br />loanPeriodPrincipalAndInterest.loanStatus | string (enum) | Options *repayment*, *deferred*
student | object | Information about the student.
student.enrollmentId | string |  The student's enrollment ID.
student.isBorrower | boolean | Whether the student is the borrower.
student.firstName | string | The student's first name.
student.middleName | string | The student's middle name.
student.lastName | string | The student's last name.
student.ssn | string | The student's social security number.
student.externalReferenceId | string | A unique identifier for the student record.
student.schoolName | string | The name of the school.
student.schoolCode | string | The school code for the school that the student is attending (or plans to attend).
student.programCode | string | The school program code for the school program that the student is attending (or plans to attend).
student.status | string (enum) | The student's enrollment status Options *Full Time*, *Three Quarter Time*, *Half Time*, *Less than Half Time*, *Leave of Absence*, *Graduated*, *Withdrawn*, *Deceased*, *Never*, *Enrolled*
student.graduationDate  | string | The student's projected graduation date.
steps | object |
steps.borrowers | object |
steps.borrowers.ids | string |
steps.borrowesrs.returnIdName | string |
steps.borrowers.errors | string |
steps.borrowers.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.borrowers.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.borrowers.payloads | |
steps.borrowers.requests | |
steps.ssoBorrowers | object |
steps.ssoBorrowers.ids | |
steps.ssoBorrowers.returnIdName | |
steps.ssoBorrowers.errors | |
steps.ssoBorrowers.status | |
steps.ssoBorrowers.validationStatus | |
steps.ssoBorrowers.payloads | |
steps.ssoBorrowers.requests | |
steps.loan | object |
steps.loan.ids | |
steps.loan.returnIdName | string |
steps.loan.errors | |
steps.loan.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.loan.validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.loan.payloads | |
steps.loan.requests | |
steps.bankProfiles | object |
steps.bankProfiles.ids | |
steps.bankProfiles.<br />returnIdName | string |
steps.bankProfiles.<br />errors | |
steps.bankProfiles.<br />status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.bankProfiles.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.bankProfiles.<br />payloads | |
steps.bankProfiles.<br />requests | |
steps.autoDebits | object |
steps.autoDebits.<br />ids | |
steps.autoDebits.<br />returnIdName | string |
steps.autoDebits.<br />errors | |
steps.autoDebits.<br />status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.autoDebits<br />.validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.autoDebits.<br />payloads | |
steps.autoDebits.<br />requests | |
steps.CellPhoneConsents | object |
steps.CellPhoneConsents.<br />ids | |
steps.CellPhoneConsents.<br />returnIdName | string |
steps.CellPhoneConsents.<br />errors | |
steps.CellPhoneConsents.<br />status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.CellPhoneConsents.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.CellPhoneConsents.<br />payloads | |
steps.CellPhoneConsents.<br />requests | |
steps.wallets | object |
steps.wallets.ids | |
steps.wallets.<br />returnIdName | string |
steps.wallets.errors | |
steps.wallets.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.wallets.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.wallets.payloads | |
steps.wallets.requests | |
steps.references | object |
steps.references.ids | |
steps.references.<br />returnIdName | string |
steps.references.errors | |
steps.references.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.references.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.references.payloads | |
steps.references.requests | |
steps.student | object
steps.student.ids | |
steps.student.<br />returnIdName | string |
steps.student.errors | |
steps.student.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.student.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.student.payloads | |
steps.student.requests | |
steps.callBack | object |
steps.callBack.ids | |
steps.callBack.<br />returnIdName | string |
steps.callBack.errors | |
steps.callBack.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.callBack.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.callBack.payloads | |
steps.callBack.requests | |
steps.completed | object |
steps.completed.ids | |
steps.completed.<br />returnIdName | string |
steps.completed.errors | |
steps.completed.status | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.completed.<br />validationStatus | string (enum) | Options *Pending*, *Failure*, *Skipped*, *Success*
steps.completed.payloads | |
steps.completed.requests | |
|||
createdBy | string | User who created the onboarding request.
createdDate | string | Date the onboarding record was created.
updatedBy | string | User who updated the onboarding request.
updatedDate | string | Date the onboarding record was updated.
isLoanCancelled | |
loanCancelledReason | string |
