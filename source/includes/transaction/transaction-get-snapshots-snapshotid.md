<!--Endpoint introduction -->
## Get Transaction Snapshot by Snapshot ID

### GET /transactions/snapshot{snapshotid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/transactionapi/transactions/snapshot/37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/transactionapi/transactions/snapshot/37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
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

xhr.open("GET", "https://api.nelnet.io/transactionapi/transactions/snapshot/37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");

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
  'Authorization': '<ACCESS TOKEN>'
}
conn.request("GET", "/transactionapi/transactions/snapshot/37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "transactionId": "1b69e362-5b34-41e6-8868-77b3cddf1249",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "transactionType": "PAYMENT",
            "feeType": "",
            "transactionDate": "2020-08-06",
            "transactionAmount": 3,
            "principalAmount": 0,
            "interestAmount": 16.05,
            "feeAmount": 0,
            "principalPaid": 0,
            "interestPaid": 3,
            "feePaid": 0,
            "principalBalance": 10000,
            "interestBalance": 131.83,
            "feeBalance": 0,
            "isCash": false,
            "transactionReferenceId": "7da7697d-2b77-49f2-886a-5356937604cb",
            "reason": null,
            "createdDate": "2020-08-06T12:53:26.212Z",
            "updatedDate": "2020-08-06T12:53:26.212Z",
            "snapshotId": "37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4",
            "loanInfo": {
                "nextDueDate": "2020-10-25",
                "termFrequency": "monthly",
                "nextStatementDate": "2020-10-04",
                "partialPaymentAmount": 0
            },
            "snapshotDate": "2020-08-06 12:59:18.000",
            "lenderFeeAmount": 0,
            "servicerFeeAmount": 0,
            "investorFeeAmount": 0,
            "lenderFeePaid": 0,
            "servicerFeePaid": 0,
            "investorFeePaid": 0,
            "lenderFeeBalance": 0,
            "servicerFeeBalance": 0,
            "investorFeeBalance": 0,
            "createdBy": {},
            "updatedBy": {}
        },
        {
            "transactionId": "37753ecd-d8f7-48bb-bb0c-d7b7aeefe7eb",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "transactionType": "PAYMENT",
            "feeType": "",
            "transactionDate": "2020-08-06",
            "transactionAmount": 5.33,
            "principalAmount": 0,
            "interestAmount": 0,
            "feeAmount": 0,
            "principalPaid": 0,
            "interestPaid": 5.33,
            "feePaid": 0,
            "principalBalance": 10000,
            "interestBalance": 126.5,
            "feeBalance": 0,
            "isCash": false,
            "transactionReferenceId": "e2bb9376-5466-405b-8dfc-2a25739cbb01",
            "reason": null,
            "createdDate": "2020-08-06T12:53:48.773Z",
            "updatedDate": "2020-08-06T12:53:48.773Z",
            "snapshotId": "37d8cb94-3a7d-4a4a-ba70-d0fccd1fbfc4",
            "loanInfo": {
                "nextDueDate": "2020-10-25",
                "termFrequency": "monthly",
                "nextStatementDate": "2020-10-04",
                "partialPaymentAmount": 0
            },
            "snapshotDate": "2020-08-06 12:59:18.000",
            "lenderFeeAmount": 0,
            "servicerFeeAmount": 0,
            "investorFeeAmount": 0,
            "lenderFeePaid": 0,
            "servicerFeePaid": 0,
            "investorFeePaid": 0,
            "lenderFeeBalance": 0,
            "servicerFeeBalance": 0,
            "investorFeeBalance": 0,
            "createdBy": {},
            "updatedBy": {}
        }
    ],
    "after": [
        {
            "transactionId": "7d94f3ff-8682-46d9-a202-ffdbfbe4d66d",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "transactionType": "INTERESTACCRUAL",
            "feeType": "",
            "transactionDate": "2020-08-01",
            "transactionAmount": 118.78,
            "principalAmount": 0,
            "interestAmount": 118.78,
            "feeAmount": 0,
            "principalPaid": 0,
            "interestPaid": 0,
            "feePaid": 0,
            "principalBalance": 10000,
            "interestBalance": 118.78,
            "feeBalance": 0,
            "isCash": null,
            "transactionReferenceId": null,
            "reason": null,
            "createdDate": "2020-08-01T01:02:22.548Z",
            "updatedDate": "2020-08-06T12:59:24.518Z",
            "loanInfo": {
                "nextDueDate": "2020-07-25",
                "termFrequency": "monthly",
                "nextStatementDate": "2020-07-04",
                "partialPaymentAmount": 0
            },
            "snapshotDate": "2020-08-10 03:02:22.141",
            "lenderFeeAmount": 0,
            "servicerFeeAmount": 0,
            "investorFeeAmount": 0,
            "lenderFeePaid": 0,
            "servicerFeePaid": 0,
            "investorFeePaid": 0,
            "lenderFeeBalance": 0,
            "servicerFeeBalance": 0,
            "investorFeeBalance": 0
        },
        {
            "transactionId": "37753ecd-d8f7-48bb-bb0c-d7b7aeefe7eb",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "transactionType": "PAYMENT",
            "feeType": "",
            "transactionDate": "2020-08-06",
            "transactionAmount": 5.33,
            "principalAmount": 0,
            "interestAmount": 0,
            "feeAmount": 0,
            "principalPaid": 0,
            "interestPaid": 5.33,
            "feePaid": 0,
            "principalBalance": 10000,
            "interestBalance": 126.5,
            "feeBalance": 0,
            "isCash": false,
            "transactionReferenceId": "e2bb9376-5466-405b-8dfc-2a25739cbb01",
            "reason": null,
            "createdDate": "2020-08-06T12:53:48.773Z",
            "updatedDate": "2020-08-06T12:59:27.297Z",
            "loanInfo": {
                "nextDueDate": "2020-07-25",
                "termFrequency": "monthly",
                "nextStatementDate": "2020-07-04",
                "partialPaymentAmount": 3
            },
            "snapshotDate": "2020-08-10 03:02:22.142",
            "lenderFeeAmount": 0,
            "servicerFeeAmount": 0,
            "investorFeeAmount": 0,
            "lenderFeePaid": 0,
            "servicerFeePaid": 0,
            "investorFeePaid": 0,
            "lenderFeeBalance": 0,
            "servicerFeeBalance": 0,
            "investorFeeBalance": 0
        }
    ]
}
```

<!-- LEFT: documentation -->

**Returns a list of transaction snapshots by loan.**

### HTTP Request

`GET https://api.nelnet.io/transactionapi/transactions/snapshot/{loanid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan.
snapshotdate | no | string | Date to search for snapshots from.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
loanId | string | The identifier for the loan.
snapshotId | string | The transaction snapshot identifier.
snapshotDate | string | The date that the transaction snapshot was created.