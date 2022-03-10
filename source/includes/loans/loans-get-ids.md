<!--Endpoint introduction -->
## Get Loan IDs

### GET /loans/ids

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/loanapi/loans/ids \
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
var client = new RestClient("https://api.nelnet.io/loanapi/loans/ids");
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

xhr.open("GET", "https://api.nelnet.io/loanapi/loans/ids");
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
    'User-Agent': "PostmanRuntime/7.18.0",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Postman-Token': "455c2deb-f977-4cf4-8fc4-f6a6f3bca7a8,6b925a86-10be-461e-b458-110e4ac5749d",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "loanapi,loans,ids", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "tenantId": "314",
            "servicerId": "2",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "loanProgramId": "756feb5d-91a1-4830-8ec0-e990788b37f4",
            "loanId": "7ff93bb1-6e6f-45ec-84d7-de0c48f7b659",
            "borrowers": [
                {
                    "borrowerId": "9ffca9e7-b2db-478c-9f57-21ce45bf965a",
                    "borrowerType": "borrower"
                }
            ]
        },
        {
            "tenantId": "314",
            "servicerId": "2",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "loanProgramId": "50023379-ef51-4262-b428-84865cd20f41",
            "loanId": "05780f01-0a86-4740-bc93-68bac6461c3c",
            "borrowers": [
                {
                    "borrowerId": "4cd98485-122c-4c1d-9a9b-7aa645e37314",
                    "borrowerType": "borrower"
                }
            ]
        }
    ],
    "paging": {
        "rows": 24252,
        "pages": 1213,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/loans/ids?offset=0&limit=20",
            "last": "/loans/ids?offset=24240&limit=20",
            "next": "/loans/ids?offset=20&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns all loan IDs.**

### HTTP Request

`GET https://api.nelnet.io/loanapi/loans/ids`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
lenderid | no | string | The identifier for the lender.
loanprogramid | no | string | The identifier for the loan program.
borrowerid | no | string | The identifier for the borrower.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
lenderId | string | The identifier for the lender.
loanProgramId | string | The identifier for the loan program.
loanId | string | The identifier for the loan.
borrowers | object | Information about the borrower.
borrowers.borrowerId | string |The identifier for the borrower.
borrowers.borrowerType | enum | Options: *borrower, co-borrower*.
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
