<!--Endpoint introduction -->
## Get Calls

### GET /calltracking/calls

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/calltrackingapi/calltracking/calls?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6' \
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
var client = new RestClient("https://api.nelnet.io/calltrackingapi/calltracking/calls?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

xhr.open("GET", "https://api.nelnet.io/calltrackingapi/calltracking/calls?loanid=2c809e08-a5ba-4559-9c1c-4ac2555fb1e6");
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

conn.request("GET", "calltrackingapi,calltracking,calls", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
  "paging": {
    "offset": 0,
    "limit": 0,
    "links": {
      "first": "string",
      "last": "string",
      "previous": "string",
      "next": "string"
    }
  },
  "data": [
    {
      "callId": "string",
      "tenantId": "string",
      "servicerId": "string",
      "loanId": "string",
      "borrowerId": "string",
      "phoneNumber": "string",
      "callStatus": "Attempted",
      "callTimestamp": "2020-08-03T21:53:31.468Z",
      "createdDate": "2020-08-03T21:53:31.468Z",
      "updatedDate": "2020-08-03T21:53:31.468Z",
      "updatedBy": {},
      "createdBy": {}
    }
  ]
}
```

<!-- LEFT: documentation -->

**Get all calls.**

### HTTP Request

`GET https://api.nelnet.io/calltrackingapi/calltracking/calls`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
loanid | no | string | The GUID identifier for the loan within Velocity.
borrowerid | no | string | The identifier (within Velocity) for the borrower.
phonenumber | no | string | The phone number of the records to return.
startdate | no | string | The starting date of the call timestamp to search for.
enddate | no | string | The end date of the call timestamp to search for.
offset | no | number | The starting record in the return - the offset between the records returned and list of total records. Defaults to 0.
limit | no | number | The number of records per page. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
offset | number | The starting record in the return - the offset between the records returned and list of total records.
limit | number | The number of records per page.
links | object | Information about the pagination and links in the response.
links.first | string | A link to the first page of records returned.
links.last | string | A link to the last page of records returned.
links.previous | string | A link to the previous page in the list of records returned.
links.next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following is contained within `data`.
callId | string | The unique, GUID identifier for the call.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
loanId | string | The loan identifier.
borrowerId | string | The identifier (within Velocity) for the borrower.
phoneNumber | string | The phone number dialed.
callStatus | enum | Result of the call. Options: *Attempted, Contacted*.
callTimestamp | date | The time that the call was made.
createdDate | date | The date that the records were created.
updatedDate | date | The date that the records last updated.
updatedBy | string | The Velocity user account that last updated records returned.
createdBy | string | The Velocity user account that created the records returned.