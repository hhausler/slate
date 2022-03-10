<!--Endpoint introduction -->
## Onboard Income Share Agreements

### POST /onboarding/bundles/incomeshare

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request POST 'https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/incomeshare' \
--header 'cache-control: no-cache' \
--header 'Content-Type: application/json' \
--header 'Authorization: BEARER <ACCESS TOKEN>' \
--data-raw '{
    "loanProgramId": "string",
    "lenderId": "string",
    "student": {
        "ssn": "string",
        "status": "Full Time",
        "lastName": "string",
        "firstName": "string",
        "isBorrower": true,
        "schoolCode": "string",
        "schoolName": "string",
        "programCode": "string",
        "graduationDate": "string"
    },
    "borrowers": [
        {
            "annualIncome": 0,
            "firstName": "string",
            "lastName": "string",
            "suffix": "string",
            "dob": "string",
            "ssn": "string",
            "customData": {},
            "externalReferenceId": "string",
            "walletId": "string",
            "bankProfiles": [
                {
                  "bankProfileName": "string",
                  "routingNumber": "string",
                  "accountingNumber": "string",
                  "accountType": "checking",
                  "accountHolderFirstName": "string",
                  "accountHolderLastName ": "string",
                  "isAutoDebit": true
                }
            ]
           "autoDebit": {
                "terms ": {
                     "type ": "HTML",
                     "content ": "string"
                 },
                "isActive": true
            },
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
            "borrowerType": "borrower",
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
            "activeMilitary": true,
            "emailAddresses": [
                {
                    "isPrimary": true,
                    "emailAddress": "string"
                }
            ]
            "references": [
               {
                  "firstName": "string",
                  "lastName": "string",
                  "middleName": "string",
                   "street1": "string",
                   "street2": "string",
                   "city": "string",
                   "state": "string",
                   "postalCode": "string",
                   "countryCode": "string",
                   "phoneNumber": "string",
                   "emailAddress": "string",
                  }
            ]
        }
    ],
    "loan": {
        "externalReferenceId": "string",
        "term": 0,
        "rateType": "Fixed",
        "loanNumber": "string",
        "customData": {},
        "Investors": [
            {
              "InvestorId": "string"
            }
        ],
        "loanPeriods": [
            {
                "deferment": {
                    "startDate": "string",
                    "loanStatus": "deferred",
                    "reduceTerm": true,
                    "capInterestAtStart": true,
                    "loanPeriodTags": [
                        "deferred"
                    ],
                    "reportingStatus": "string"
                }
            },
            {
                "incomeBasedRepayment": {
                    "startDate": "string",
                    "loanStatus": "repayment",
                    "reduceTerm": true,
                    "firstPaymentDate": "string",
                    "loanPeriodTags": [
                        "Repayment"
                    ],
                    "reportingStatus": "string"
                }
            }
        ],
        "interestRate": 0,
        "disbursements": [
            {
                "fees": 0,
                "feeType": "capped",
                "principal": 0,
                "disbursementDate": "string"
            },
            {
                "fees": 0,
                "feeType": "capped",
                "principal": 0,
                "disbursementDate": "string"
            }
        ],
        "incomeSharePercentage": 0
    }
}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/incomeshare");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESSTOKEN");
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
var body = @"{" + "\n" +
@"    ""student"": {" + "\n" +
@"        ""isBorrower"": true," + "\n" +
@"        ""firstName"": ""string""," + "\n" +
@"        ""middleName"": ""string""," + "\n" +
@"        ""lastName"": ""string""," + "\n" +
@"        ""ssn"": ""string""," + "\n" +
@"        ""externalReferenceId"": ""string""," + "\n" +
@"        ""schoolName"": ""string""," + "\n" +
@"        ""schoolCode"": ""string""," + "\n" +
@"        ""programCode"": ""string""," + "\n" +
@"        ""status"": ""Full Time""," + "\n" +
@"        ""graduationDate"": ""string""" + "\n" +
@"    }," + "\n" +
@"    ""loanProgramId"": ""string""," + "\n" +
@"    ""lenderId"": ""string""," + "\n" +
@"    ""itemId"": ""string""," + "\n" +
@"    ""batchId"": ""string""," + "\n" +
@"    ""callBackURL"": ""string""," + "\n" +
@"    ""borrowers"": [" + "\n" +
@"        {" + "\n" +
@"            ""annualIncome"": 0," + "\n" +
@"            ""borrowerId"": ""string""," + "\n" +
@"            ""firstName"": ""string""," + "\n" +
@"            ""middleName"": ""string""," + "\n" +
@"            ""lastName"": ""string""," + "\n" +
@"            ""suffix"": ""string""," + "\n" +
@"            ""score"": ""string""," + "\n" +
@"            ""ssn"": ""string""," + "\n" +
@"            ""dob"": ""string""," + "\n" +
@"            ""addresses"": [" + "\n" +
@"                {" + "\n" +
@"                    ""street1"": ""string""," + "\n" +
@"                    ""street2"": ""string""," + "\n" +
@"                    ""city"": ""string""," + "\n" +
@"                    ""state"": ""string""," + "\n" +
@"                    ""postalCode"": ""string""," + "\n" +
@"                    ""countryCode"": ""string""," + "\n" +
@"                    ""isPrimary"": true" + "\n" +
@"                }" + "\n" +
@"            ]," + "\n" +
@"            ""phoneNumbers"": [" + "\n" +
@"                {" + "\n" +
@"                    ""phoneNumber"": ""string""," + "\n" +
@"                    ""isPrimary"": true," + "\n" +
@"                    ""isMobile"": true," + "\n" +
@"                    ""hasCellPhoneConsent"": true," + "\n" +
@"                    ""type"": ""home""" + "\n" +
@"                }" + "\n" +
@"            ]," + "\n" +
@"            ""emailAddresses"": [" + "\n" +
@"                {" + "\n" +
@"                    ""emailAddress"": ""string""," + "\n" +
@"                    ""isPrimary"": true" + "\n" +
@"                }" + "\n" +
@"            ]," + "\n" +
@"            ""customData"": {}," + "\n" +
@"            ""activeMilitary"": true," + "\n" +
@"            ""activePrivacy"": true," + "\n" +
@"            ""externalReferenceId"": ""string""," + "\n" +
@"            ""borrowerNumber"": ""string""," + "\n" +
@"            ""ecorrAccepted"": true," + "\n" +
@"            ""walletId"": ""string""," + "\n" +
@"            ""bankProfiles"": [" + "\n" +
@"                {" + "\n" +
@"                    ""bankProfileName"": ""string""," + "\n" +
@"                    ""routingNumber"": ""string""," + "\n" +
@"                    ""accountNumber"": ""string""," + "\n" +
@"                    ""accountType"": ""Checking""," + "\n" +
@"                    ""accountHolderFirstName"": ""string""," + "\n" +
@"                    ""accountHolderLastName"": ""string""," + "\n" +
@"                    ""isAutoDebit"": true" + "\n" +
@"                }" + "\n" +
@"            ]," + "\n" +
@"            ""autoDebit"": {" + "\n" +
@"                ""terms"": {" + "\n" +
@"                    ""type"": ""HTML""," + "\n" +
@"                    ""content"": ""string""" + "\n" +
@"                }," + "\n" +
@"                ""isActive"": true" + "\n" +
@"            }," + "\n" +
@"            ""references"": [" + "\n" +
@"                {" + "\n" +
@"                    ""firstName"": ""string""," + "\n" +
@"                    ""middleName"": ""string""," + "\n" +
@"                    ""lastName"": ""string""," + "\n" +
@"                    ""street1"": ""string""," + "\n" +
@"                    ""street2"": ""string""," + "\n" +
@"                    ""city"": ""string""," + "\n" +
@"                    ""state"": ""string""," + "\n" +
@"                    ""postalCode"": ""string""," + "\n" +
@"                    ""countryCode"": ""string""," + "\n" +
@"                    ""phoneNumber"": ""string""," + "\n" +
@"                    ""emailAddress"": ""string""" + "\n" +
@"                }" + "\n" +
@"            ]," + "\n" +
@"            ""activeOfac"": true," + "\n" +
@"            ""borrowerType"": ""string""" + "\n" +
@"        }" + "\n" +
@"    ]," + "\n" +
@"    ""loan"": {" + "\n" +
@"        ""incomeSharePercentage"": 0," + "\n" +
@"        ""disbursements"": [" + "\n" +
@"            {" + "\n" +
@"                ""principal"": 0," + "\n" +
@"                ""fees"": 0," + "\n" +
@"                ""feeType"": ""capped""," + "\n" +
@"                ""externalReferenceId"": ""string""," + "\n" +
@"                ""disbursementDate"": ""string""" + "\n" +
@"            }" + "\n" +
@"        ]," + "\n" +
@"        ""loanPeriods"": [" + "\n" +
@"            {" + "\n" +
@"                ""fixedAmount"": {" + "\n" +
@"                    ""paymentAmount"": 0," + "\n" +
@"                    ""firstPaymentDate"": ""string""," + "\n" +
@"                    ""paymentFrequency"": ""weekly""," + "\n" +
@"                    ""capInterestAtStart"": true," + "\n" +
@"                    ""startDate"": ""string""," + "\n" +
@"                    ""reduceTerm"": true," + "\n" +
@"                    ""loanPeriodTags"": [" + "\n" +
@"                        ""string""" + "\n" +
@"                    ]," + "\n" +
@"                    ""reportingStatus"": ""string""," + "\n" +
@"                    ""loanStatus"": ""repayment""" + "\n" +
@"                }," + "\n" +
@"                ""deferment"": {" + "\n" +
@"                    ""capInterestAtStart"": true," + "\n" +
@"                    ""startDate"": ""string""," + "\n" +
@"                    ""reduceTerm"": true," + "\n" +
@"                    ""loanPeriodTags"": [" + "\n" +
@"                        ""string""" + "\n" +
@"                    ]," + "\n" +
@"                    ""reportingStatus"": ""string""," + "\n" +
@"                    ""loanStatus"": ""repayment""" + "\n" +
@"                }," + "\n" +
@"                ""incomeBasedRepayment"": {" + "\n" +
@"                    ""startDate"": ""string""," + "\n" +
@"                    ""firstPaymentDate"": ""string""," + "\n" +
@"                    ""reduceTerm"": true," + "\n" +
@"                    ""loanPeriodTags"": [" + "\n" +
@"                        ""string""" + "\n" +
@"                    ]," + "\n" +
@"                    ""reportingStatus"": ""string""," + "\n" +
@"                    ""loanStatus"": ""repayment""," + "\n" +
@"                    ""paymentFrequency"": ""weekly""" + "\n" +
@"                }" + "\n" +
@"            }" + "\n" +
@"        ]," + "\n" +
@"        ""term"": 0," + "\n" +
@"        ""interestRate"": 0," + "\n" +
@"        ""rateType"": ""Fixed""," + "\n" +
@"        ""externalReferenceId"": ""string""," + "\n" +
@"        ""loanNumber"": ""string""," + "\n" +
@"        ""customData"": {}," + "\n" +
@"        ""investors"": [" + "\n" +
@"            {" + "\n" +
@"                ""investorId"": ""string""" + "\n" +
@"            }" + "\n" +
@"        ]" + "\n" +
@"    }" + "\n" +
@"}";
```

```javascript
var data = JSON.stringify({
  "student": {
    "isBorrower": true,
    "firstName": "string",
    "middleName": "string",
    "lastName": "string",
    "ssn": "string",
    "externalReferenceId": "string",
    "schoolName": "string",
    "schoolCode": "string",
    "programCode": "string",
    "status": "Full Time",
    "graduationDate": "string"
  },
  "loanProgramId": "string",
  "lenderId": "string",
  "itemId": "string",
  "batchId": "string",
  "callBackURL": "string",
  "borrowers": [
    {
      "annualIncome": 0,
      "borrowerId": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "suffix": "string",
      "score": "string",
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
      "activeOfac": true,
      "borrowerType": "string"
    }
  ],
  "loan": {
    "incomeSharePercentage": 0,
    "disbursements": [
      {
        "principal": 0,
        "fees": 0,
        "feeType": "capped",
        "externalReferenceId": "string",
        "disbursementDate": "string"
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
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment"
        },
        "deferment": {
          "capInterestAtStart": true,
          "startDate": "string",
          "reduceTerm": true,
          "loanPeriodTags": [
            "string"
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment"
        },
        "incomeBasedRepayment": {
          "startDate": "string",
          "firstPaymentDate": "string",
          "reduceTerm": true,
          "loanPeriodTags": [
            "string"
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment",
          "paymentFrequency": "weekly"
        }
      }
    ],
    "term": 0,
    "interestRate": 0,
    "rateType": "Fixed",
    "externalReferenceId": "string",
    "loanNumber": "string",
    "customData": {},
    "investors": [
      {
        "investorId": "string"
      }
    ]
  }
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;
xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
xhr.open("POST", "https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/incomeshare");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Authorization", "<ACCESSTOKEN>");
xhr.setRequestHeader("cache-control", "no-cache");
xhr.send(data);
```

```python
import http.client
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = json.dumps({
  "student": {
    "isBorrower": True,
    "firstName": "string",
    "middleName": "string",
    "lastName": "string",
    "ssn": "string",
    "externalReferenceId": "string",
    "schoolName": "string",
    "schoolCode": "string",
    "programCode": "string",
    "status": "Full Time",
    "graduationDate": "string"
  },
  "loanProgramId": "string",
  "lenderId": "string",
  "itemId": "string",
  "batchId": "string",
  "callBackURL": "string",
  "borrowers": [
    {
      "annualIncome": 0,
      "borrowerId": "string",
      "firstName": "string",
      "middleName": "string",
      "lastName": "string",
      "suffix": "string",
      "score": "string",
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
          "isPrimary": True
        }
      ],
      "phoneNumbers": [
        {
          "phoneNumber": "string",
          "isPrimary": True,
          "isMobile": True,
          "hasCellPhoneConsent": True,
          "type": "home"
        }
      ],
      "emailAddresses": [
        {
          "emailAddress": "string",
          "isPrimary": True
        }
      ],
      "customData": {},
      "activeMilitary": True,
      "activePrivacy": True,
      "externalReferenceId": "string",
      "borrowerNumber": "string",
      "ecorrAccepted": True,
      "walletId": "string",
      "bankProfiles": [
        {
          "bankProfileName": "string",
          "routingNumber": "string",
          "accountNumber": "string",
          "accountType": "Checking",
          "accountHolderFirstName": "string",
          "accountHolderLastName": "string",
          "isAutoDebit": True
        }
      ],
      "autoDebit": {
        "terms": {
          "type": "HTML",
          "content": "string"
        },
        "isActive": True
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
      "activeOfac": True,
      "borrowerType": "string"
    }
  ],
  "loan": {
    "incomeSharePercentage": 0,
    "disbursements": [
      {
        "principal": 0,
        "fees": 0,
        "feeType": "capped",
        "externalReferenceId": "string",
        "disbursementDate": "string"
      }
    ],
    "loanPeriods": [
      {
        "fixedAmount": {
          "paymentAmount": 0,
          "firstPaymentDate": "string",
          "paymentFrequency": "weekly",
          "capInterestAtStart": True,
          "startDate": "string",
          "reduceTerm": True,
          "loanPeriodTags": [
            "string"
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment"
        },
        "deferment": {
          "capInterestAtStart": True,
          "startDate": "string",
          "reduceTerm": True,
          "loanPeriodTags": [
            "string"
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment"
        },
        "incomeBasedRepayment": {
          "startDate": "string",
          "firstPaymentDate": "string",
          "reduceTerm": True,
          "loanPeriodTags": [
            "string"
          ],
          "reportingStatus": "string",
          "loanStatus": "repayment",
          "paymentFrequency": "weekly"
        }
      }
    ],
    "term": 0,
    "interestRate": 0,
    "rateType": "Fixed",
    "externalReferenceId": "string",
    "loanNumber": "string",
    "customData": {},
    "investors": [
      {
        "investorId": "string"
      }
    ]
  }
})
headers = {
  'Content-Type': 'application/json',
  'cache-control': 'no-cache',
  'Authorization': '<ACCESSTOKEN>,
}
conn.request("POST", "/onboardingapi-v2/onboarding/bundles/incomeshare", payload, headers)
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

**Use this endpoint to add a new income share agreement and a new borrower/participant to the system. The borrower object's fields are required unless you want to add a new loan to an existing borrower's record. To add a new loan, pass a borrowerID and the rest of the borrower object's fields will be skipped.**

### HTTP Request

`POST https://api.nelnet.io/onboardingapi-v2/onboarding/bundles/incomeshare`

The request must contain the `body` object, made up of the following parameters.

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
student | yes | object | Information about the student associated with the agreement to be onboarded.
student.isBorrower | yes | boolean | Whether the student associated with the agreement is also the participant on the loan.
student.firstName | yes | string | The student's first name.
student.middleName | no | string | The student's middle name.
student.lastName | yes | string | The student's last name.
student.ssn | yes | string | The student's Social Security number.
student.<br />externalReferenceId | no | string | An optional external reference identifier for the student.
student.schoolName | yes | string | The name of the school that the student is attending (or plans to attend).
student.schoolCode | yes | string | The school code for the school that the student is attending (or plans to attend).
student.programCode | yes | string | The school program code for the school program that the student is attending (or plans to attend).
student.status | yes | string(enum) | The student's enrollment status. Options: *Full Time, Three Quarter Time, Half Time, Less than Half Time, Leave of Absence, Graduated, Withdrawn, Deceased, Never Enrolled*.
student.graduationDate | yes | string | The student's projected graduation date.
loanProgramId | yes | string | The identifier for the loan program associated with the agreement to be onboarded.
lenderId | yes | string | The identifier for the lender associated with the agreement to be onboarded.
itemId | no | string | Optional parameter on the GET command, generally intended to be unique. It allows groups and batches to be defined by the user according to provided values.
batchId | no | string | Optional parameter on the GET command. It allows groups and batches to be defined by the user according to provided values.
callBackURL | no | string | A user specified a URL. Notification of the end of the onboarding process is sent to this address.
borrowers | yes | object | Information about the borrower(s) associated with the loan to be onboarded.
borrower.annualIncome | yes | number | The borrower's annual gross income.
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
borrower.phoneNumbers.type | yes | string(enum) | The phone number type. Options: *home, work, other*.
borrower.emailAddresses | no | object | Information about the phone email address(es) associated with the borrower.
borrower.emailAddresses.<br />emailAddress | yes | string | The email address.
borrower.emailAddresses.<br />isPrimary | yes | boolean | Whether this email address is known to be the borrower's primary address.
borrower.customData | no | object | Optional additional information about the borrower.
borrower.activeMilitary | yes | boolean | Whether the borrower is an active military servicemember.
borrower.activePrivacy | yes | boolean | Whether the borrower actively enrolled in privacy protection.
borrower.<br />externalReferenceId | no | string | An optional external reference identifier for the borrower.
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
borrower.autoDebit.<br />terms | yes | object | Information about auto debit terms of use.
borrower.autoDebit.<br />terms. type | yes | string(enum) | The term type for auto debit. Options: *HTML, ID, Text, URL*.
borrower.autoDebit.<br />terms.content | yes | string | The content of the auto debit terms.
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
loan.incomeSharePercentage | yes | number | Percentage of the gross income a borrower will need to pay each month of the payment term.
loan.term | yes | integer($int32) | The loan's term.
loan.interestRate | yes | number($double) | The loan's interest rate.
loan.rateType | yes | string(enum) | The interest rate type for the loan. Options: *Fixed, Variable*.
loan.externalReferenceId | no | string | An optional external reference identifier for the loan.
loan.loanNumber | no | string | An optional identifier for the loan.
loan.customData | no | object | Optional additional information about the loan.
loan.investors | no | object | Information about investor(s) associated with the loan.
loan.investor.investorId | yes | string | Identifier for the investor.
loan.disbursements | yes | object | Information about disbursements associated with the loan.
loan.disbursement.<br />externalReferenceId | no | string | An optional external reference identifier for the disbursement.
loan.disbursement.<br />disbursementDate | yes | string | The disbursement date.
loan.disbursement.<br />principal | yes | number($double) | The disbursement amount.
loan.disbursement.<br />fees | no | number | the amount of the disbursement fees.
loan.disbursement.<br />feeType | no | string (enum) | The type of disbursement feeds (capped or deducte).
loan.loanPeriods | yes | object | Information about loan periods.
loan.loanPeriod.<br />fixedAmount | no | object | Information about fixed amount loan periods.
loan.loanPeriod.<br />fixedAmount.<br />paymentAmount | yes | number($double) | The payment amount.
loan.loanPeriod.<br />fixedAmount.<br />firstPaymentDate | yes | string | The date that the first payment is due.
loan.loanPeriod.<br />fixedAmount.<br />paymentFrequency | no | string(enum) | The frequency at which payments are required. Options: *weekly, bi-weekly, monthly, quarterly*.
loan.loanPeriod.<br />fixedAmount.<br />capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />fixedAmount.<br />startDate | yes | string | The starting date for the loan period.
loan.loanPeriod.<br />fixedAmount.<br />reduceTerm | yes | boolean | Whether the payment reduces the term of the loan.
loan.loanPeriod.<br />fixedAmount.<br />loanPeriodTags | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />fixedAmount.<br />reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />fixedAmount.<br />loanStatus | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />deferment | no | object | Information about deferment loan periods.
loan.loanPeriod.<br />deferment.<br />capInterestAtStart | no | boolean | Whether interest is capped at the start of the loan period.
loan.loanPeriod.<br />deferment.<br />startDate | yes | string | The loan period start date.
loan.loanPeriod.<br />deferment.<br />educeTerm | yes | boolean | Whether the loan period reduces the term.
loan.loanPeriod.<br />deferment.<br />loanPeriodTags | no | string | The loan period tags.
loan.loanPeriod.<br />deferment.<br />reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />deferment.<br />loanStatus | no | string(enum) | Options: *repayment, deferred*.
loan.loanPeriod.<br />incomeBasedRepayment | no | object | Income based repayment.
loan.loanPeriod.<br />incomeBasedRepayment.<br />firstPaymentDate | yes | string | The date that the first payment is due.
loan.loanPeriod.<br />incomeBasedRepayment.<br />paymentFrequency | no | string(enum) | The frequency at which payments are required. Options: *weekly, bi-weekly, monthly, quarterly*.
loan.loanPeriod.<br />incomeBasedRepayment.<br />startDate | yes | string | The loan period start date.
loan.loanPeriod.<br />incomeBasedRepayment.<br />reduceTerm | yes | boolean | Whether the loan period reduces the term.
loan.loanPeriod.<br />incomeBasedRepayment.<br />loanPeriodTags | no | string | The loan period tags.
loan.loanPeriod.<br />incomeBasedRepayment.<br />reportingStatus | no | string | The reporting status.
loan.loanPeriod.<br />incomeBasedRepayment.<br />loanStatus | no | string(enum) | Options: *repayment, deferred*.


### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The onboarding response.
data.onboardingId | string | The onboarding ID for the loan onboarded.
data.itemId | string | The item ID.
data.batchId | string | The batch ID.
data.createdDate | string($date-time) | The created date, the date that the loan was onboarded.
