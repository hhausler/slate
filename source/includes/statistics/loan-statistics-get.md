<!--Endpoint introduction -->
## Get Loan Statistics

### GET /loan-statistics

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/statisticsapi/loan-statistics?includepaymentdetails=true&includefeedetails=true&loanid=00000000-0000-0000-0000-000000000000' \
--header 'Authorization: <ACCESSTOKEN>'
```

```csharp
var client = new RestClient("https://api.nelnet.io/statisticsapi/loan-statistics?includepaymentdetails=true&includefeedetails=true&loanid=00000000-0000-0000-0000-000000000000");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Authorization", "<ACCESSTOKEN>");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;
 
xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
 
xhr.open("GET", "https://api.nelnet.io/statisticsapi/loan-statistics?includepaymentdetails=true&includefeedetails=true&loanid=00000000-0000-0000-0000-000000000000");
xhr.setRequestHeader("Authorization", "<ACCESSTOKEN>");
 
xhr.send();
```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = ''
headers = {
  'Authorization': '<ACCESSTOKEN>'
}
conn.request("GET", "/statisticsapi/loan-statistics?includepaymentdetails=true&includefeedetails=true&loanid=00000000-0000-0000-0000-000000000000", payload, headers)
res = conn.getresponse()
data = res.read()
```

> JSON returned:

```json
{
  "data": {
    "loanId": "string",
    "loanNumber": "string",
    "term": 0,
    "billingCyclesCompleted": 0,
    "disbursementDate": "string",
    "firstPaymentDate": "string",
    "status": "string",
    "termFrequency": "string",
    "externalReferenceId": "string",
    "totalNumberOfPayments": 0,
    "totalAmountOfPayments": 0,
    "totalNumberOfFees": 0,
    "totalAmountOfFees": 0,
    "paymentDetails": [
      {
        "amount": 0,
        "dueDate": "string",
        "effectiveDate": "string",
        "source": "string",
        "type": "string"
      }
    ],
    "feeDetails": [
      {
        "amount": 0,
        "date": "string",
        "type": "string"
      }
    ]
  }
}
```

<!-- LEFT: documentation -->

**Get data about a loan.**

Use this endpoint to get statistics on a given loan, including payment details and fee details.

### HTTP Request

`GET https://api.nelnet.io/statisticsapi/loan-statistics`

The request must have at least one of the following query parameters: `loanid`, `externalreferenceid`, or `loannumber`.

Parameter | Type | Description
----------| ------- | -------
loanid | string | The GUID identifier for a loan.
externalreferenceid | string | The loan's external reference ID.
loannumber | string | The "friendly" loan number.
includepaymentdetails | boolean | Determines if payment details information (one record per payment made on the loan) is included in the response. Defaults to *false*.
includefeedetails | boolean | Determines if fee details information is included in the response. Defaults to *false*.

### HTTP Response

`ResponseBodyLoanStatistic` contains the object `data`, which contains the following.

Field Name | Type | Description
---------- | ------- | -------
loanId | string | The GUID identifier for the loan.
loanNumber | string | The "friendly" loan number.
term | number($double) | The loan's term.
billingCyclesCompleted | number($double) | The number of billing cycles completed from the loan's
disbursementDate | string | The loan's original disbursement date.
firstPaymentDate | string | The date that the first payment on the loan was due.
status | string | The loan's status.
termFrequency | string | The interval at which payments are due. Options: *bi-weekly, monthly, quarterly, weekly*.
externalReferenceId	| string | The loan's external reference ID.
totalNumberOfPayments | number($double) | The total number of payments made to date.
totalAmountOfFees | number($double) | The total amount of fees paid to date.

**Payment Details**

The `paymentDetails` object is only included in the response if `includepaymentdetails` was set to *true* in the request. One object per payment will be posted.

Field Name | Type | Description
---------- | ------- | -------
paymentDetails.amount | number($double) | The total amount paid in the payment being detailed in this record.
paymentDetails.dueDate | string | The next due date for the billing cycle in which the payment was made.
paymentDetails.effectiveDate | string | The effective date of the payment being detailed in this record.
paymentDetails.source | string | The payment source of the payment being detailed in this record.
paymentDetails.type	| string | The payment type of the payment being detailed in this record.

**Fee Details**

The `feeDetails` object is only included in the response if `includefeedetails` was set to *true* in the request.

Field Name | Type | Description
---------- | ------- | -------
feeDetails.amount | number($double) | The total amount of fees paid.
feeDetails.date	| string | The date that the fee amount was paid.
feeDetails.type	| string | The fee type assessed.