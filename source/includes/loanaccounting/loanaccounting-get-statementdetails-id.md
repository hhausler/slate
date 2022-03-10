<!--Endpoint introduction -->
## Get Statement Details for a Given Statement

### GET /statementdetails/{statementId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanaccountingapi/statementdetails/c713985a-9645-4880-913f-1230cf4e4d6b' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/statementdetails/c713985a-9645-4880-913f-1230cf4e4d6b");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/statementdetails/c713985a-9645-4880-913f-1230cf4e4d6b");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "Bearer <ACCESS TOKEN>");

xhr.send(data);
```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = ''
headers = {
  'tenantid': '314',
  'servicerid': '2',
  'Authorization': 'Bearer <ACCESS TOKEN>'
}
conn.request("GET", "/loanaccountingapi/statementdetails/c713985a-9645-4880-913f-1230cf4e4d6b", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "statementId": "c713985a-9645-4880-913f-1230cf4e4d6b",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "statementDate": "2020-01-31",
        "nextDueDate": "2020-02-13",
        "currentAmountDue": 85,
        "pastAmountDue": 1272,
        "feeAmountDue": 15,
        "totalAmountDue": 1372,
        "createdDate": "2020-01-31T11:01:33.919Z",
        "updatedDate": "2020-01-31T11:01:33.919Z",
        "scanline": "5625577569840964620200213001372001",
        "payoffAmount": 2395.22,
        "lastPaymentDate": "2019-12-23",
        "lastPaymentAmount": 1,
        "regularPaymentAmount": 85,
        "amountPaidCurrentCycle": 0,
        "daysLate": 197,
        "projectedLateFeeDate": "2020-02-24",
        "projectedLateFeeAmount": 10,
        "remainingTerm": 0,
        "interestRate": 30,
        "perDiemAmount": 1.64,
        "pricipalBalance": 2000,
        "interestBalance": 343.85,
        "feeBalance": 15,
        "projectedInterestAccrued": 21.37,
        "totalInterestAccrued": 346.85,
        "totalAmountPaid": 3,
        "sinceLastStatement": {
            "interestRate": 30,
            "interestAccrued": 23.02,
            "lateFees": 15,
            "nsfFees": 0,
            "amountPaid": 0,
            "appliedToPrincipal": 0,
            "appliedToInterest": 0,
            "appliedToFees": 0
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns statement details by statement.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/statementdetails{statementId}`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
statementId | yes | string (path parameter) | The identifier for the statement.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
payoffAmount | number | Payoff amount as of the next due date.
lastPaymentAmount | number | Amount of last payment made.
lastPaymentDate | string | Date of last payment made.
regularPaymentAmount | number | Regularly scheduled monthly payment amount.
amountPaidCurrentCycle | number | Amount already paid this month (i.e., amount that goes towards satisfying current amount due).
daysLate | number | Numbers of days past due.
projectedLateFeeDate | string | The nextDueDate + grace days (i.e., the date a late fee will be assessed if no payment made).
projectedLateFeeAmount | number | The projected amount of late fees that will be assessed as of the above date.
remainingTerm | number | Remaining term as of the statement date.
interestRate | number | Interest rate as of the current statement date.
perDiemAmount | number | The daily interest amount as of the statement date.
pricipalBalance | number | The principal balance as of the statement date.
interestBalance | number | The outstanding unpaid interest as of the statement date.
feeBalance | number | The outstanding fees as of the statement date.
projectedInterestAccrued | number | The estimated interest that will accrue between statementDate and nextDueDate.
totalInterestAccrued | number | The total interest accrued since the first disbursement date (as of statementDate).
totalAmountPaid | number | The total amount paid since first disbursement.
sinceLastStatement | object | Statement detail information since last statement date.
sinceLastStatement.interestRate | number | Interest rate on previous statement.
sinceLastStatement.interestAccrued | number | Interest accrued between previous statement date and current statement date.
sinceLastStatement.lateFees | number | Late fees assessed since previous statement.
sinceLastStatement.nsfFees | number | Insufficient funds (NSF) fees assessed since previous statement.
sinceLastStatement.amountPaid | number | Total amount paid since previous statement.
sinceLastStatement.appliedToPrincipal | number | Amount applied to principal since previous statement.
sinceLastStatement.appliedToInterest | number | Amount applied to interest since previous statement.
sinceLastStatement.appliedToFees | number | Amount applied to fees since previous statement.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
statementId | string | The identifier for the statement.
loanId | string | The identifier for the loan.
statementDate | string | The next statement date for the loan.
nextDueDate | string | The next payment due date for the loan.
currentAmountDue | number | Amount due on the next due date.
pastAmountDue | number | Past amount due.
feeAmountDue | number | Fee amount due.
totalAmountDue | number | Total amount due.
scanline | string | A unique identifier for the statement, used to associate a statement and payment.
createdDate | date | The date that the statement records were created.
updatedDate | date | The date that the statement records were last updated.