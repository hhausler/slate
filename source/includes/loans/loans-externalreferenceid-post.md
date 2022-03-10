<!--Endpoint introduction -->
## Update a Loan's External Reference ID

### POST /loans/externalreferenceid/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request POST 'https://api.nelnet.io/loanapi/loans/externalreferenceid/00000000-0000-0000-0000-000000000000' \
--header 'Content-Type: application/json' \
--header 'Authorization: <ACCESSTOKEN>' \
--data-raw '{
  "externalReferenceId": "New External Reference ID String or NULL"
}'

```

```csharp
var client = new RestClient("https://api.nelnet.io/loanapi/loans/externalreferenceid/00000000-0000-0000-0000-000000000000");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESSTOKEN>");
request.AddParameter("application/json", "{\n  \"externalReferenceId\": \"New External Reference ID String or NULL\"\n}",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);

```

```javascript
var data = JSON.stringify({"externalReferenceId":"New External Reference ID String or NULL"});
 
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;
 
xhr.addEventListener("readystatechange", function() {
 if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
 
xhr.open("POST", "https://api.nelnet.io/loanapi/loans/externalreferenceid/00000000-0000-0000-0000-000000000000");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Authorization", "<ACCESSTOKEN>");
 
xhr.send(data);

```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = "{\n  \"externalReferenceId\": \"New External Reference ID String or NULL\"\n}"
headers = {
  'Content-Type': 'application/json',
  'Authorization': '<ACCESSTOKEN>'
}
conn.request("POST", "/loanapi/loans/externalreferenceid/00000000-0000-0000-0000-000000000000", payload, headers)
res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
  "data": {
    "loanId": "string",
    "loanNumber": "string",
    "loanNumberFormatted": "string",
    "tenantId": "string",
    "servicerId": "string",
    "borrowers": [
      {
        "borrowerId": "string",
        "borrowerType": "borrower"
      }
    ],
    "investors": [
      {
        "investorId": "string"
      }
    ],
    "loanProgramId": "string",
    "lenderId": "string",
    "term": 0,
    "amount": 0,
    "interestRate": 0,
    "minInterestRate": 0,
    "maxInterestRate": 0,
    "margin": 0,
    "rateType": "string",
    "dueDay": 0,
    "disbursementDate": "string",
    "firstPaymentDate": "string",
    "status": "charge off",
    "termFrequency": "monthly",
    "externalReferenceId": "string",
    "onboardingId": "string",
    "customData": {},
    "createdDate": "2020-03-09T16:46:50.017Z",
    "updatedDate": "2020-03-09T16:46:50.017Z",
    "updatedBy": {},
    "createdBy": {},
    "isActive": true,
    "isScraActive": true,
    "isBankruptcyActive": true,
    "isDeathActive": true,
    "isDisabilityActive": true,
    "originationFee": 0,
    "paymentScheduleType": "fixed term",
    "paymentAmount": 0
  }
}

```

<!-- LEFT: documentation -->

**Update an external reference ID for an existing loan.**

Call this endpoint to add or replace a loan's external reference ID.

### HTTP Request

`POST https://api.nelnet.io/loanapi/loans/externalreferenceid/{loanid}`

Parameter | Required | Type | Description
----------| -------- | ---- | -----------
loanid | yes | string | The loan's identifier. (Path parameter.)
externalReferenceId | yes | string | The new external reference ID to assign to the loan. (Body parameter.)

### HTTP Response

The response object `PagedResponseBodyLoan` contains the object `data`. `data` contains the object `loan`, which contains the following.

Field Name | Type | Description
---------- | ------- | -------
loanId | string | The GUID loan identifier.
loanNumber | string | The "friendly ID" for the loan within Velocity.
loanNumberFormatted | string | The formatted loan number.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
borrowers | object | Information about the borrower(s) associated with the loan(s) returned.
borrowers.borrowerId | string | The identifier (within Velocity) for the borrower.
borrowers.borrowerType | enum | Options: *borrower, co-borrower*.
investors | object | Information about investors.
investorId | string | The identifier(s) for investor(s) associated with the loan(s) returned.
loanProgramId | string | The identifier for the loan program.
lenderId | string | The identifier for the lender(s) associated with the loan(s) returned.
term | integer($int32) | The loan term.
amount | number($double) | The total loan amount.
interestRate | number($double) | The loan interest rate.
minInterestRate | number($double) | The minimum interest rate for the loan(s) returned.
maxInterestRate | number($double) | The maximum interest rate for the loan(s) returned.
margin | number($double) | The loan margin amount. For fixed-term loans, this will be set to 0.
rateType | string | The loan rate type, either *fixed* or *variable*.
dueDay | number($double) | The payment due day for the loan(s).
disbursementDate | string | The date on which the loan funds were disbursed to the borrower, in the *YYYY-MM-DD* format.
firstPaymentDate | string | The borrower's first payment due date, in the *YYYY-MM-DD* format.
status | enum | The current loan status. Options: *charge off, default, forbearance, fraud, paid in full, rejected, repayment, write off*.
termFrequency | enum | The term frequency of the loan. Options: *monthly, bi-weekly, weekly, quarterly*.
externalReferenceId | string | The external identifier or reference number for the borrower.
onboardingId | string | The identifier for the onboarding bundle assigned when the borrower was added (via call to the Onboarding service) to Velocity.
customData | object | Contains any custom data fields added to the loan record.
createdDate | string($date-time) | Date on which the loan record was created.
updatedDate | string($date-time) | Date on which the borrower record was last updated, if applicable.
updatedBy | object | The identifier for the token associated with the latest update, if any.
createdBy | object | The identifier for the token associated with the loan creation.
isActive | boolean | Shows whether the loan is in active status.
isScraActive | boolean | Shows whether the loan has an active servicemember flag.
isBankruptcyActive | boolean | Shows whether the loan has an active bankruptcy flag.
isDeathActive | boolean | Shows whether the loan has an active death flag.
isDisabilityActive | boolean | Shows whether the loan has an active disability flag.
originationFee | number($double) | The fee, if any, charged at the time of origination.
paymentAmount | number($double) | The amount of the payment regularly due for the loan.