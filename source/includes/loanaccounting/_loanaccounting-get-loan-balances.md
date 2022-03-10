<!--Endpoint introduction -->
## Get Loan Balances

### GET /loanaccounting/loanbalances

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/loanaccountingapi/loanbalances?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6' \
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
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/loanbalances?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/loanbalances?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

conn.request("GET", "loanaccountingapi,loanbalances", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "totalPrincipalAmount": 2000,
        "totalInterestAmount": 374.79,
        "totalFeeAmount": 30,
        "totalPrincipalPaid": 2000,
        "totalInterestPaid": 374.79,
        "totalFeePaid": 30,
        "principalBalance": 0,
        "interestBalance": 0,
        "feeBalance": 0,
        "effectiveDate": "2020-08-03",
        "accrueToDate": "2020-02-17",
        "lastPaymentDate": "2020-02-17",
        "originationFee": 0,
        "additionalInterest": 0,
        "interestRate": 30,
        "perDiem": {
            "amount": 0,
            "interestRate": 30,
            "interestMethod": "actual/365"
        },
        "totalLenderFeeAmount": 30,
        "totalServicerFeeAmount": 0,
        "totalInvestorFeeAmount": 0,
        "totalLenderFeePaid": 30,
        "totalServicerFeePaid": 0,
        "totalInvestorFeePaid": 0,
        "lenderFeeBalance": 0,
        "servicerFeeBalance": 0,
        "investorFeeBalance": 0
    }
}
```

<!-- LEFT: documentation -->

**Returns all running balances related to principal, interest and fees for a given loan.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/loanbalances`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The GUID identifier for the loan within Velocity.
effectivedate | no | string | The effective date for the information to return.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
loanId | string | The GUID identifier for the loan within Velocity.
totalPrincipalAmount | number | The total principal amount due on the loan.
totalInterestAmount | number | The total amount of all interest charged over the history of the loan.
totalFeeAmount | number | The total amount of all fees charged over the history of the loan.
totalPrincipalPaid | number | The total principal paid over the history of the loan.
totalInterestPaid | number | The total interest paid over the history of the loan.
totalFeePaid | number | The total fees paid over the history of the loan.
principalBalance | number | The principal balance, as of the effective date.
interestBalance | number | The total interest amount due, as of the effective date.
feeBalance | number | The total amount of fees due, as of the effective date.
effectiveDate | string | The effective date for the information returned.
accrueToDate | string | The date that the `interestBalance` has accrued to.
lastPaymentDate | string | The date that the most recent payment was made.
originationFee | number | The fee, if any, charged at the time of origination.
additionalInterest | number | The amount that will accrue on the loan from `accrueToDate` to `effectiveDate`. `effectiveDate` defaults to the current date if no value is provided.
interestRate | number | The loan's interest rate at the time of calculation.
perDiem | object | Information about the daily interest rate and interest accrual.
perDiem.amount | number | The amount, in interest, added to the total amount due for the loan, based on the daily interest accrual.
perDiem.interestRate | number | The daily interest rate.
perDiem.interestMethod | string | The daily interest accrual method. Options are *actual/actual, 30/360, actual/365, actual/365.25.*
totalLenderFeeAmount | number | The total amount of lender fees accrued.
totalServicerFeeAmount | number | The total amount of servicer fees accrued.
totalInvestorFeeAmount | number | The total amount of investor fees accrued.
totalLenderFeePaid | number | The total amount of lender fees paid.
totalServicerFeePaid | number | The total amount of servicer fees paid.
totalInvestorFeePaid | number | The total amount of investor fees paid.
lenderFeeBalance | number | The balance (remaining due amount) for lender fees.
servicerFeeBalance | number | The balance (remaining due amount) for servicer fees.
investorFeeBalance | number | The balance (remaining due amount) for investor fees.