<!--Endpoint introduction -->
## Get Last Payment

### GET /payments/last

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/transactionapi/payments/last?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6' \
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
var client = new RestClient("https://api.nelnet.io/transactionapi/payments/last?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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
var settings = {
  "async": true,
  "crossDomain": true,
  "url": "https://api.nelnet.io/transactionapi/payments/last?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
  "method": "GET",
  "headers": {
    "tenantid": "314",
    "servicerid": "2",
    "Authorization": "<ACCESS TOKEN>",
    "Accept": "*/*",
    "Cache-Control": "no-cache",
    "Host": "api.nelnet.io",
    "Accept-Encoding": "gzip, deflate",
    "Connection": "keep-alive",
    "cache-control": "no-cache"
  }
}

$.ajax(settings).done(function (response) {
  console.log(response);
});
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

conn.request("GET", "transactionapi,payments,last", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "transactionId": "90c2f0bf-2b86-4419-9c83-7fb51cafce70",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "transactionType": "PAYMENT",
        "feeType": "",
        "transactionDate": "2020-02-17",
        "transactionAmount": 2401.79,
        "principalAmount": 0,
        "interestAmount": 26.3,
        "feeAmount": 0,
        "principalPaid": 2000,
        "interestPaid": 371.79,
        "feePaid": 30,
        "principalBalance": 0,
        "interestBalance": 0,
        "feeBalance": 0,
        "isCash": false,
        "transactionReferenceId": "20fe8a54-b1dc-44bf-9008-ad6494037785",
        "reason": null,
        "loanInfo": {
            "nextDueDate": "2019-07-18",
            "nextStatementDate": "2020-02-28",
            "partialPaymentAmount": 3
        },
        "lenderFeeAmount": 0,
        "servicerFeeAmount": 0,
        "investorFeeAmount": 0,
        "lenderFeePaid": 30,
        "servicerFeePaid": 0,
        "investorFeePaid": 0,
        "lenderFeeBalance": 0,
        "servicerFeeBalance": 0,
        "investorFeeBalance": 0,
        "createdDate": "2020-02-17T13:32:41.582Z",
        "updatedDate": "2020-02-17T13:32:41.582Z"
    }
}
```

<!-- LEFT: documentation -->

**Returns last payment made for a loan.**

### HTTP Request

`GET https://api.nelnet.io/transactionapi/payments/last`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The unique identifier for the loan.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
transactionId | string | Unique identifer (GUID) for the transaction.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
transactionDate | string | Date of transaction.
transactionType | enum | Type of transaction. Options: *CHARGEOFF, CONVERSION, DISBURSEMENT, DISBURSEMENTADJUSTMENT, FEE, FEEREVERSAL, INTERESTACCRUAL, INTERESTCAP, PAYMENT, PAYMENTREVERSAL*.
feeType | enum | Type of fee charged, if any. Options: *LATE, NSF, ORIGINATION*.
transactionAmount | number | Amount of transaction.
principalAmount | number | Amount of the transaction that is applied to the principal balance (can be a positive or negative amount).
interestAmount | number | Amount of the transaction that is applied to the interest balance (can be a positive or negative amount).
feeAmount | number | Amount of the transaction that is applied to the balance of fees due.
principalPaid | number | Total principal paid.
interestPaid | number | Total interest paid.
feePaid | number | Total fees paid.
principalBalance | number | Remaining principal due.
interestBalance | number | Remaining interest due.
feeBalance | number | Remaining fees due.
isCash | boolean | Indicates whether the payment is considered a cash payment. Almost all borrower initiated payments are cash, but there are cases where a loan would need a non-cash transaction applied to a loan.
transactionReferenceId | string | Unique reference identifier for the transaction.
reason | string | Reason for the transaction.
loanInfo | object | Information about the loan. 
loanInfo.nextDueDate | string | The next payment due date for the loan.
loanInfo.nextStatementDate | string | The next statement date for the loan.
loanInfo.partialPaymentAmount | number | The loan's partial payment amount.
loanInfo.loanProgramId | string | The identifier for the loan program.
loanInfo.termFrequency | string | The loan's term frequency.
lenderFeeAmount | number | Outstanding lender fees due.
servicerFeeAmount | number | Outstanding servicer fees due.
investorFeeAmount | number | Outstanding investor fees due.
lenderFeePaid | number | Total lender fees paid.
servicerFeePaid | string | Total servicer fees paid.
investorFeePaid | number | Total investor fees paid.
lenderFeeBalance | number | Remaining lender fees due.
servicerFeeBalance | number | Remaining servicer fees due.
investorFeeBalance | number | Remaining investor fees due.
createdDate | date | Date that the transaction was created.
updatedDate | date | Date that the transaction was last updated.
isBackDated | boolean | Indicates whether the transaction was back-dated.
snapshotId | string | Identifier for the snapshot.