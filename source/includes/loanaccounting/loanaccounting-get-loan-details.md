<!--Endpoint introduction -->
## Get Loan Accounting Details

### GET loanaccounting/loandetails

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/loanaccountingapi/loandetails?loanid=c2d6aa46-ab71-475d-943a-dec948f99843' \
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
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/loandetails?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/loandetails?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

conn.request("GET", "loanaccountingapi,loandetails", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
        "principalBalance": 10000,
        "nextDueDate": "2020-09-25",
        "currentAmountDue": 0,
        "pastAmountDue": 0,
        "feeAmountDue": 0,
        "totalAmountDue": 0,
        "lastPaymentDate": null,
        "paidToDate": "2020-10-25",
        "defaultDate": null,
        "interestBalance": 125.2,
        "perDiem": {
            "amount": 3.21,
            "interestRate": 11.75,
            "interestMethod": "actual/actual"
        },
        "daysLate": 0,
        "regularPaymentAmount": 161.16,
        "remainingTerm": 96,
        "termFrequency": "monthly",
        "lenderFeeAmountDue": 0,
        "servicerFeeAmountDue": 0,
        "investorFeeAmountDue": 0,
        "partialPaymentAmount": 0
    }
}
```

<!-- LEFT: documentation -->

**Returns loan detail information for a loan.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/loandetails`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The GUID identifier for the loan within Velocity.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
loanId | string | The GUID identifier for the loan within Velocity.
principalBalance | number | The total current principal balance, as of today.
interestBalance | number | The total interest amount due, as of today.
nextDueDate | string | The current billing cycle’s due date.
currentAmountDue | number | Amount due on the next due date.
pastAmountDue | number | Past-due amount on the next due date.
feeAmountDue | number | Fee amount due on the next due date.
totalAmountDue | number | Total amount due, including any past-due or fee amounts, on the next due date.
lastPaymentDate | string | Most recent payment date.
perDiem | object | Information about the daily interest rate and interest accrual.
perDiem.amount | number | The amount, in interest, added to the total amount due for the loan, based on the daily interest accrual.
perDiem.interestRate | number | The daily interest rate.
perDiem.interestMethod | string | The daily interest accrual method. Options are *actual/actual, 30/360, actual/365, actual/365.25.*
paidToDate | string | The actual next due date (representing how behind or how far ahead the loan is).
daysLate | number | Number of days that the loan is late
regularPaymentAmount | number | The regularly scheduled monthly payment amount.
remainingTerm | number | The number of payment cycles remaining to pay off the loan.
termFrequency | enum | The interval at which payments are due. Options: *bi-weekly, monthly, quarterly, weekly.* 
lenderFeeAmountDue | number | Outstanding lender fees due.
servicerFeeAmountDue | number | Outstanding servicer fees due.
investorFeeAmountDue | number | Outstanding investor fees due.
defaultDate | string | For loans that have reached a certain amount of days past due (120 or 180 are pretty common), the loan can be put in a default status. This is the date of that status change. 