<!--Endpoint introduction -->
## Get Latest Statement for a Loan

### GET /statements/latest/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/loanaccountingapi/statements/latest/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6 \
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
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/statements/latest/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/statements/latest/2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

conn.request("GET", "loanaccountingapi,statements,latest,2c809e08-a5ba-4559-9c1c-4ac2555fb1e6", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "statementId": "cddba3f7-c84f-4722-afdd-8ede30ad3440",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
        "statementDate": "2020-02-14",
        "nextDueDate": "2020-02-27",
        "currentAmountDue": 85,
        "pastAmountDue": 1357,
        "feeAmountDue": 30,
        "totalAmountDue": 1472,
        "createdDate": "2020-02-14T11:01:39.144Z",
        "updatedDate": "2020-02-14T11:01:39.144Z",
        "scanline": "5168899551801067220200227001472007"
    }
}
```

<!-- LEFT: documentation -->

**Gets the latest statement for a given loan (by loan ID).**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/statements/latest/{loanid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path) | The GUID identifier for the loan within Velocity.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
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
scanline | string | 
createdDate | date | The date that the statement records were created.
updatedDate | date | The date that the statement records were last updated.