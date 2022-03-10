<!--Endpoint introduction -->
## Get Statements

### GET /statements

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/loanaccountingapi/statements?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6' \
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
var client = new RestClient("https://api.nelnet.io/loanaccountingapi/statements?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

xhr.open("GET", "https://api.nelnet.io/loanaccountingapi/statements?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

conn.request("GET", "loanaccountingapi,statements", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
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
        },
        {
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
            "scanline": "5625577569840964620200213001372001"
        },
        {
            "statementId": "fc1ff639-009b-435a-835e-c6af612c3ce2",
            "tenantId": "314",
            "servicerId": "2",
            "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
            "statementDate": "2019-10-11",
            "nextDueDate": "2019-10-24",
            "currentAmountDue": 85,
            "pastAmountDue": 595,
            "feeAmountDue": 0,
            "totalAmountDue": 680,
            "createdDate": "2019-10-17T21:51:57.276Z",
            "updatedDate": "2019-10-17T21:51:57.276Z",
            "scanline": "5394441386526045320191024000680004"
        }
    ],
    "paging": {
        "rows": 10,
        "pages": 1,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/statements?offset=0&limit=20",
            "last": "/statements?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns all statements.**

### HTTP Request

`GET https://api.nelnet.io/loanaccountingapi/statements`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | no | string | The GUID identifier for the loan within Velocity.
scanline | string | A unique identifier for the statement, used to associate a statement and payment.
nextduedate | no | string | The next due date in the statement.
offset | no | number | The starting record in the return - the offset between the records returned and list of total records. Defaults to 0.
limit | no | number | The number of records per page. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
paging.offset | number ($double) | The starting record in the return - the offset between the records returned and list of total records.
paging.limit | number ($double) | The number of records per page.
paging.links | object | Information about the pagination and links in the response.
paging.links.first | string | A link to the first page of records returned.
paging.links.last | string | A link to the last page of records returned.
paging.links.previous | string | A link to the previous page in the list of records returned.
paging.links.next | string | A link to the next page in the list of records returned.
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
scanline | string | A unique identifier for the statement, used to associate a statement and payment.
createdDate | date | The date that the statement records were created.
updatedDate | date | The date that the statement records were last updated.