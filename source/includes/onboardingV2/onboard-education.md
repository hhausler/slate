<!--Endpoint introduction -->
## Onboard Education Loans

### POST /onboarding/bundles/education

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X POST \
  https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/consumer \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Content-Type: application/json' \
  -H 'cache-control: no-cache' \
  -d '{
    "loanProgramId": "string",
    "lenderId": "string",
    "itemId": "string",
    "batchId": "string",
    "callBackURL": "string",
    "borrowers": [
      {
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
            "hasCellPhoneConsent": true,
            "type": "home"
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
        "borrowerNumber": "string",
        "ecorrAccepted": true,
        "walletId": "string",
        "bankProfiles": [
          {
            "bankProfileName": "string",
            "routingNumber": "string",
            "accountNumber": "string",
            "accountType": "Checking",
            "accountHolderFirstName": "string",
            "accountHolderLastName": "string",
            "isAutoDebit": true
          }
        ],
        "autoDebit": {
          "terms": {
            "type": "HTML",
            "content": "string"
          },
          "isActive": true
        },
        "references": [
          {
            "firstName": "string",
            "middleName": "string",
            "lastName": "string",
            "street1": "string",
            "street2": "string",
            "city": "string",
            "state": "string",
            "postalCode": "string",
            "countryCode": "string",
            "phoneNumber": "string",
            "emailAddress": "string"
          }
        ],
        "borrowerType": "string"
      }
    ],
    "loan": {
      "term": 0,
      "interestRate": 0,
      "margin": 0,
      "rateType": "Fixed",
      "externalReferenceId": "string",
      "loanNumber": "string",
      "customData": {},
      "investors": [
        {
          "investorId": "string"
        }
      ],
      "disbursements": [
        {
          "externalReferenceId": "string",
          "disbursementDate": "string",
          "amount": 0,
          "originationFee": 0
        }
      ],
      "loanPeriods": [
        {
          "fixedAmount": {
            "paymentAmount": 0,
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "deferment": {
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "interestOnly": {
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "principalAndInterest": {
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          }
        }
      ]
    }
  }
```

```csharp
var client = new RestClient("https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/consumer");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddParameter("undefined", "{ \"loanProgramId\": \"string\", \"lenderId\": \"string\", \"itemId\": \"string\", \"batchId\": \"string\", \"callBackURL\": \"string\", \"borrowers\": [ { \"borrowerId\": \"string\", \"firstName\": \"string\", \"middleName\": \"string\", \"lastName\": \"string\", \"suffix\": \"string\", \"ssn\": \"string\", \"dob\": \"string\", \"addresses\": [ { \"street1\": \"string\", \"street2\": \"string\", \"city\": \"string\", \"state\": \"string\", \"postalCode\": \"string\", \"countryCode\": \"string\", \"isPrimary\": true } ], \"phoneNumbers\": [ { \"phoneNumber\": \"string\", \"isPrimary\": true, \"isMobile\": true, \"hasCellPhoneConsent\": true, \"type\": \"home\" } ], \"emailAddresses\": [ { \"emailAddress\": \"string\", \"isPrimary\": true } ], \"customData\": {}, \"activeMilitary\": true, \"activePrivacy\": true, \"externalReferenceId\": \"string\", \"borrowerNumber\": \"string\", \"ecorrAccepted\": true, \"walletId\": \"string\", \"bankProfiles\": [ { \"bankProfileName\": \"string\", \"routingNumber\": \"string\", \"accountNumber\": \"string\", \"accountType\": \"Checking\", \"accountHolderFirstName\": \"string\", \"accountHolderLastName\": \"string\", \"isAutoDebit\": true } ], \"autoDebit\": { \"terms\": { \"type\": \"HTML\", \"content\": \"string\" }, \"isActive\": true }, \"references\": [ { \"firstName\": \"string\", \"middleName\": \"string\", \"lastName\": \"string\", \"street1\": \"string\", \"street2\": \"string\", \"city\": \"string\", \"state\": \"string\", \"postalCode\": \"string\", \"countryCode\": \"string\", \"phoneNumber\": \"string\", \"emailAddress\": \"string\" } ], \"borrowerType\": \"string\" } ], \"loan\": { \"term\": 0, \"interestRate\": 0, \"margin\": 0, \"rateType\": \"Fixed\", \"externalReferenceId\": \"string\", \"loanNumber\": \"string\", \"customData\": {}, \"investors\": [ { \"investorId\": \"string\" } ], \"disbursements\": [ { \"externalReferenceId\": \"string\", \"disbursementDate\": \"string\", \"amount\": 0, \"originationFee\": 0 } ], \"loanPeriods\": [ { \"fixedAmount\": { \"paymentAmount\": 0, \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"deferment\": { \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"interestOnly\": { \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"principalAndInterest\": { \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] } } ] }}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```javascript
var data = JSON.stringify({
  {
    "loanProgramId": "string",
    "lenderId": "string",
    "itemId": "string",
    "batchId": "string",
    "callBackURL": "string",
    "borrowers": [
      {
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
            "hasCellPhoneConsent": true,
            "type": "home"
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
        "borrowerNumber": "string",
        "ecorrAccepted": true,
        "walletId": "string",
        "bankProfiles": [
          {
            "bankProfileName": "string",
            "routingNumber": "string",
            "accountNumber": "string",
            "accountType": "Checking",
            "accountHolderFirstName": "string",
            "accountHolderLastName": "string",
            "isAutoDebit": true
          }
        ],
        "autoDebit": {
          "terms": {
            "type": "HTML",
            "content": "string"
          },
          "isActive": true
        },
        "references": [
          {
            "firstName": "string",
            "middleName": "string",
            "lastName": "string",
            "street1": "string",
            "street2": "string",
            "city": "string",
            "state": "string",
            "postalCode": "string",
            "countryCode": "string",
            "phoneNumber": "string",
            "emailAddress": "string"
          }
        ],
        "borrowerType": "string"
      }
    ],
    "loan": {
      "term": 0,
      "interestRate": 0,
      "margin": 0,
      "rateType": "Fixed",
      "externalReferenceId": "string",
      "loanNumber": "string",
      "customData": {},
      "investors": [
        {
          "investorId": "string"
        }
      ],
      "disbursements": [
        {
          "externalReferenceId": "string",
          "disbursementDate": "string",
          "amount": 0,
          "originationFee": 0
        }
      ],
      "loanPeriods": [
        {
          "fixedAmount": {
            "paymentAmount": 0,
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "deferment": {
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "interestOnly": {
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          },
          "principalAndInterest": {
            "firstPaymentDate": "string",
            "paymentFrequency": "weekly",
            "capInterestAtStart": true,
            "startDate": "string",
            "reduceTerm": true,
            "loanPeriodTags": [
              "string"
            ]
          }
        }
      ]
    }
  }
})

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
payload = "{ \"loanProgramId\": \"string\", \"lenderId\": \"string\", \"itemId\": \"string\", \"batchId\": \"string\", \"callBackURL\": \"string\", \"borrowers\": [ { \"borrowerId\": \"string\", \"firstName\": \"string\", \"middleName\": \"string\", \"lastName\": \"string\", \"suffix\": \"string\", \"ssn\": \"string\", \"dob\": \"string\", \"addresses\": [ { \"street1\": \"string\", \"street2\": \"string\", \"city\": \"string\", \"state\": \"string\", \"postalCode\": \"string\", \"countryCode\": \"string\", \"isPrimary\": true } ], \"phoneNumbers\": [ { \"phoneNumber\": \"string\", \"isPrimary\": true, \"isMobile\": true, \"hasCellPhoneConsent\": true, \"type\": \"home\" } ], \"emailAddresses\": [ { \"emailAddress\": \"string\", \"isPrimary\": true } ], \"customData\": {}, \"activeMilitary\": true, \"activePrivacy\": true, \"externalReferenceId\": \"string\", \"borrowerNumber\": \"string\", \"ecorrAccepted\": true, \"walletId\": \"string\", \"bankProfiles\": [ { \"bankProfileName\": \"string\", \"routingNumber\": \"string\", \"accountNumber\": \"string\", \"accountType\": \"Checking\", \"accountHolderFirstName\": \"string\", \"accountHolderLastName\": \"string\", \"isAutoDebit\": true } ], \"autoDebit\": { \"terms\": { \"type\": \"HTML\", \"content\": \"string\" }, \"isActive\": true }, \"references\": [ { \"firstName\": \"string\", \"middleName\": \"string\", \"lastName\": \"string\", \"street1\": \"string\", \"street2\": \"string\", \"city\": \"string\", \"state\": \"string\", \"postalCode\": \"string\", \"countryCode\": \"string\", \"phoneNumber\": \"string\", \"emailAddress\": \"string\" } ], \"borrowerType\": \"string\" } ], \"loan\": { \"term\": 0, \"interestRate\": 0, \"margin\": 0, \"rateType\": \"Fixed\", \"externalReferenceId\": \"string\", \"loanNumber\": \"string\", \"customData\": {}, \"investors\": [ { \"investorId\": \"string\" } ], \"disbursements\": [ { \"externalReferenceId\": \"string\", \"disbursementDate\": \"string\", \"amount\": 0, \"originationFee\": 0 } ], \"loanPeriods\": [ { \"fixedAmount\": { \"paymentAmount\": 0, \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"deferment\": { \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"interestOnly\": { \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] }, \"principalAndInterest\": { \"firstPaymentDate\": \"string\", \"paymentFrequency\": \"weekly\", \"capInterestAtStart\": true, \"startDate\": \"string\", \"reduceTerm\": true, \"loanPeriodTags\": [ \"string\" ] } } ] }}"
headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Content-Type': "application/json",
    'cache-control': "no-cache"
    }
conn.request("POST", "onboardingapi-v2,onboarding,bundles,consumer", payload, headers)
res = conn.getresponse()
data = res.read()
```
> JSON returned:

```json
{
    "data": {
        "onboardingId": "GUID",
        "itemId": "string",
        "batchId": "string",
        "createdDate": "1970-01-01T00:00:0.000Z"
    }
}
```

<!-- LEFT: documentation -->

**Use this endpoint to add a new education loan and a new borrower to the system. The borrower object's fields are required unless you want to add a new loan to an existing borrower's record. To add a new loan, pass a borrowerID and the rest of the borrower object's fields will be skipped.**

### HTTP Request

`POST https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/education`

The request must contain the `body` object, made up of the following parameters.

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
student | yes | object | Information about the student associated with the loan to be onboarded.
student.isBorrower | yes | boolean | Whether the student associated with the loan is also the borrower on the loan.
student.firstName | yes | string | The student's first name.
student.middleName | no | string | The student's middle name.
student.lastName | yes | string | The student's last name.
student.ssn | yes | string | The student's Social Security number.
student.externalReferenceId | no | string | An optional external reference identifier for the student.
student.schoolName | yes | string | The name of the school that the student is attending (or plans to attend).
student.schoolCode | yes | string | The school code for the school that the student is attending (or plans to attend).
student.programCode | yes | string | The school program code for the school program that the student is attending (or plans to attend).
student.status | yes | string(enum) | The student's enrollment status. Options: *Full Time, Three Quarter Time, Half Time, Less than Half Time, Leave of Absence, Graduated, Withdrawn, Deceased, Never Enrolled*.
student.graduationDate | yes | string | The student's projected graduation date.
loanProgramId | yes | string | The identifier for the loan program associated with the loan to be onboarded.
lenderId | yes | string | The identifier for the lender associated with the loan to be onboarded.
itemId | no | string | Optional parameter on the GET command, generally intended to be unique. It allows groups and batches to be defined by the user according to provided values.
batchId | no | string | Optional parameter on the GET command. It allows groups and batches to be defined by the user according to provided values.
callBackURL | no | string | A user specified a URL. Notification of the end of the onboarding process is sent to this address.
borrowers | yes | object | Information about the borrower(s) associated with the loan to be onboarded.
borrower.borrowerId | no | string | The identifier for the borrower.
borrower.firstName | yes | string | The borrower's first name.
borrower.middleName | no | string | The borrower's middle name.
borrower.lastName | yes | string | The borrower's last name.
borrower.suffix | no | string | The borrower's name suffix, if applicable.
borrower.ssn | yes | string | The borrower's Social Security number.
borrower.dob | yes | string | The borrower's date of birth.
borrower.addresses | yes | object | Information about address(es) associated with the borrower.
borrower.address.<br />street1 | yes | string | The address's first street line.
borrower.address.<br />street2 | yes | string | The address's second street line.
borrower.address.<br />city | yes | string | The address's city.
borrower.address.<br />state | yes | string | The address's state.
borrower.address.<br />postalCode | yes | string | The address's postal code.
borrower.address.<br />countryCode | yes | string | The address's country code.
borrower.address.<br />isPrimary | yes | boolean | Whether this address is known to be the borrower's primary address.
borrower.phoneNumbers | yes | object | Information about the phone number(s) associated with the borrower.
borrower.phoneNumbers.<br />phoneNumber | yes | string | The phone number.
borrower.phoneNumbers.<br />isPrimary | yes | boolean | Whether this phone number is known to be the borrower's primary phone number.
borrower.phoneNumbers.<br />isMobile | yes | boolean | Whether this phone number is a mobile phone.
borrower.phoneNumbers.<br />hasCellPhoneConsent | yes | boolean | Whether the borrower has provided cell phone consent for this phone number.
borrower.phoneNumbers.t<br />ype | yes | string(enum) | The phone number type. Options: *home, work, other*.
borrower.<br />emailAddresses | no | object | Information about the phone email address(es) associated with the borrower.
borrower.<br />emailAddresses.<br />emailAddress | yes | string | The email address.
borrower.<br />emailAddresses.isPrimary | yes | boolean | Whether this email address is known to be the borrower's primary address.
borrower.customData | no | object | Optional additional information about the borrower.
borrower.activeMilitary | yes | boolean | Whether the borrower is an active military servicemember.
borrower.activePrivacy | yes | boolean | Whether the borrower actively enrolled in privacy protection.
borrower.externalReferenceId | no | string | An optional external reference identifier for the borrower.
borrower.borrowerNumber | no | string | The borrower number.
borrower.ecorrAccepted | yes | boolean | Whether the borrower has accepted the terms for electronic correspondence.
borrower.walletId | no | boolean | The identifier for the wallet associated with the borrower.
borrower.bankProfiles | no | object | Information about any bank profiles saved for the borrower.
borrower.<br />bankProfiles.<br />bankProfileName | no | string | An optional profile name.
borrower.<br />bankProfiles.<br />routingNumber | yes | string | The routing number for the bank account saved in the bank profile.
borrower.<br />bankProfiles.<br />accountNumber | yes | string | The account number for the bank account.
borrower.<br />bankProfiles.<br />accountType | yes | string(enum) | The account type of the bank account. Options: *Checking, Savings*.
borrower.<br />bankProfiles.<br />accountHolderFirstName | yes | string | The account holder's first name.
borrower.<br />bankProfiles.<br />accountHolderLastName | yes | string | The account holder's last name.
borrower.<br />bankProfiles.<br />isAutoDebit | yes | boolean | Whether the account is set up for auto debit.
borrower.autoDebit | no | object | Information about auto debit settings.
borrower.<br />autoDebit.<br />terms | yes | object | Information about auto debit terms of use.
borrower.<br />autoDebit.<br />terms.<br />type | yes | string(enum) | The term type for auto debit. Options: *HTML, ID, Text, URL*.
borrower.<br />autoDebit.<br />terms.<br />content | yes | string | The content of the auto debit terms.
borrower.autoDebit.<br />isActive | yes | boolean | Whether auto debit is currently active for the borrower.
borrower.references | no | object | Information about reference(s) for the borrower.
borrower.reference.<br />firstName | yes | string | The reference's first name.
borrower.reference.<br />middleName | no | string | The reference's middle name.
borrower.reference.<br />lastName | yes | string | The reference's last name.
borrower.reference.<br />street1 | no | string | The reference's address street line 1.
borrower.reference.<br />street2 | no | string | The reference's address street line 2.
borrower.reference.<br />city | no | string | The city for the reference's address.
borrower.reference.<br />state | no | string | The state for the reference's address.
borrower.reference.<br />postalCode | no | string | The postal code for the reference's address.
borrower.reference.<br />countryCode | no | string | The country code for the reference's address.
borrower.reference.<br />phoneNumber | no | string | The phone number for the reference.
borrower.reference.<br />emailAddress | no | string | The email address for the reference.
borrower.borrowerType | yes | string | The type of borrower.
loan | yes | object | Information about the loan.
loan.term | yes | integer($int32) | The loan's term.
loan.interestRate | yes | number($double) | The loan's interest rate.
loan.margin | no | number($double) | The loan's margin.
loan.rateType | yes | string(enum) | The interest rate type for the loan. Options: *Fixed, Variable*.
loan.externalReferenceId | no | string | An optional external reference identifier for the loan.
loan.loanNumber | no | string | An optional identifier for the loan.
loan.customData | no | object | Optional additional information about the loan.
loan.investors | no | object | Information about investor(s) associated with the loan.
loan.investor.investorId | yes | string | Identifier for the investor.
loan.disbursements | yes | object | Information about disbursements associated with the loan.
loan.disbursement.<br />externalReferenceId | no | string | An optional external reference identifier for the disbursement.
loan.disbursement.<br />disbursementDate | yes | string | The disbursement date.
loan.disbursement.<br />amount | yes | number($double) | The disbursement amount.
loan.disbursement.<br />originationFee | no | number($double) | The origination fee included in the disbursement.
loan.loanPeriods | yes | object | Information about loan periods.
loan.loanPeriod.<br />fixedAmount | no | object | Information about fixed amount loan periods.
loan.loanPeriod.<br />fixedAmount.paymentAmount | yes | number($double) | The payment amount.
loan.loanPeriod.<br />fixedAmount.firstPaymentDate | yes | string | The date that the first payment is due.
loan.loanPeriod.<br />fixedAmount.paymentFrequency | no | string(enum) | The frequency at which payments are required. Options: *weekly, bi-weekly, monthly, quarterly*.
loan.loanPeriod.<br />fixedAmount.<br />capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />fixedAmount.startDate | yes | string | The starting date for the loan period.
loan.loanPeriod.<br />fixedAmount.reduceTerm | yes | boolean | Whether the payment reduces the term of the loan.
loan.loanPeriod.<br />fixedAmount.loanPeriodTags | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />fixedAmount.reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />fixedAmount.loanStatus | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />deferment | no | object | Information about deferment loan periods.
loan.loanPeriod.<br />deferment.capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />deferment.startDate | yes | string | The loan period start date.
loan.loanPeriod.<br />deferment.reduceTerm | yes | boolean | Whether the loan period reduces the term.
loan.loanPeriod.<br />deferment.loanPeriodTags | no | string | The loan period tags.
loan.loanPeriod.<br />deferment.reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />deferment.loanStatus | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.interestOnly | no | object | Information about interest only loan periods.
loan.loanPeriod.<br />interestOnly.firstPaymentDate | yes | string | The date that the first payment is due.
loan.loanPeriod.<br />interestOnly.paymentFrequency | no | string(enum) | The frequency at which payments are required. Options: *weekly, bi-weekly, monthly, quarterly*.
loan.loanPeriod.<br />interestOnly.capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />interestOnly.startDate | yes | string | The loan period start date.
loan.loanPeriod.<br />interestOnly.reduceTerm | yes | boolean | Whether the loan period reduces the term.
loan.loanPeriod.<br />interestOnly.loanPeriodTags | no | string | The loan period tags.
loan.loanPeriod.<br />interestOnly.reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />interestOnly.loanStatus | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />principalAndInterest | no | object | Information about principal and interest loan periods.
loan.loanPeriod.<br />principalAndInterest.firstPaymentDate | yes | string | The date that the first payment is due.
loan.loanPeriod.<br />principalAndInterest.<br />paymentFrequency | no | string(enum) | The frequency at which payments are required. Options: *weekly, bi-weekly, monthly, quarterly*.
loan.loanPeriod.<br />principalAndInterest.<br />capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />principalAndInterest.<br />startDate | yes | string | The loan period start date.
loan.loanPeriod.<br />principalAndInterest.<br />reduceTerm | yes | boolean | Whether the loan period reduces the term.
loan.loanPeriod.<br />principalAndInterest.<br />loanPeriodTags | no | string | The loan period tags.
loan.loanPeriod.<br />principalAndInterest.<br />reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />principalAndInterest.<br />loanStatus | no | string(enum) | Options: *repayment, deferred*.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The onboarding response.
data.onboardingId | string | The onboarding ID for the loan onboarded.
data.itemId | string | The item ID.
data.batchId | string | The batch ID.
data.createdDate | string($date-time) | The created date, the date that the loan was onboarded.
