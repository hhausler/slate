<!--Endpoint introduction -->
## Get Disbursements

### GET /disbursements

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/transactionapi/disbursements?loanid=c2d6aa46-ab71-475d-943a-dec948f99843' \
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
var client = new RestClient("https://api.nelnet.io/transactionapi/disbursements?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/transactionapi/disbursements?loanid=c2d6aa46-ab71-475d-943a-dec948f99843");
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

conn.request("GET", "transactionapi,disbursements", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "transactionId": "c9d1cf90-bfc6-4bde-90e8-42f3f603d588",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "transactionType": "DISBURSEMENT",
            "feeType": "",
            "transactionDate": "2020-06-25",
            "transactionAmount": 10000,
            "principalAmount": 10000,
            "interestAmount": 0,
            "feeAmount": 0,
            "principalPaid": 0,
            "interestPaid": 0,
            "feePaid": 0,
            "principalBalance": 10000,
            "interestBalance": 0,
            "feeBalance": 0,
            "isCash": null,
            "transactionReferenceId": "",
            "reason": null,
            "loanInfo": null,
            "lenderFeeAmount": 0,
            "servicerFeeAmount": 0,
            "investorFeeAmount": 0,
            "lenderFeePaid": 0,
            "servicerFeePaid": 0,
            "investorFeePaid": 0,
            "lenderFeeBalance": 0,
            "servicerFeeBalance": 0,
            "investorFeeBalance": 0,
            "createdDate": "2020-07-23T19:43:53.415Z",
            "updatedDate": "2020-07-23T19:43:53.415Z"
        }
    ],
    "paging": {
        "rows": 1,
        "pages": 1,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/v1/disbursements?loanid=c2d6aa46-ab71-475d-943a-dec948f99843?offset=0&limit=20",
            "last": "/v1/disbursements?loanid=c2d6aa46-ab71-475d-943a-dec948f99843?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns all disbursement transactions for a loan.**

### HTTP Request

`GET https://api.nelnet.io/transactionapi/disbursements`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string | The identifier for the loan.
includeadjustments | no | boolean | 
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

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
paging | object | Information about the paging of the results returned, within the total results available.
paging.rows | string | Rows included in the records returned.
paging.pages | string | Pages included in the records returned.
paging.offset | number | The starting record in the return - the offset between the records returned and list of total records.
paging.limit | number | The number of records per page. 
paging.links | object | Information about the pagination and links in the response.
paging.links.first | string | A link to the first page of records returned.
paging.links.last | string | A link to the last page of records returned.
paging.links.previous | string | A link to the previous page in the list of records returned.
paging.links.next | string | A link to the next page in the list of records returned.