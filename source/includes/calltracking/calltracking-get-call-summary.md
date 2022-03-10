<!--Endpoint introduction -->
## Get Call Summaries

### GET /calltracking/call/summary

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/calltrackingapi/calltracking/call/summary \
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
var client = new RestClient("https://api.nelnet.io/calltrackingapi/calltracking/call/summary");
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

xhr.open("GET", "https://api.nelnet.io/calltrackingapi/calltracking/call/summary");
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

conn.request("GET", "calltrackingapi,calltracking,call,summary", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "total": "1",
            "loanId": "8c68d817-d0a5-4caf-b161-6c483d150723",
            "borrowerId": "5f424907-2c87-4cff-bcf7-5e9d255b3fda",
            "phoneNumber": "+16666666666",
            "callStatus": "Contacted",
            "minCall": "2019-09-03T15:34:57.722Z",
            "maxCall": "2019-09-03T15:34:57.722Z"
        },
        {
            "total": "1",
            "loanId": "c956d1da-bd3e-4c82-a480-eccc3ff932b9",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "phoneNumber": "+17155553210",
            "callStatus": "Attempted",
            "minCall": "2019-09-06T20:13:38.248Z",
            "maxCall": "2019-09-06T20:13:38.248Z"
        }
    ]
}
```

<!-- LEFT: documentation -->

**Get call summaries based on loan, borrower, phone number, status, start date or end date.**

### HTTP Request

`GET https://api.nelnet.io/calltrackingapi/calltracking/call-summary`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | no | string | The GUID identifier for the loan within Velocity.
borrowerid | no | string | The identifier (within Velocity) for the borrower.
phonenumber | no | string | The phone number of the records to return.
startdate | no | string | The starting date of the call timestamp to search for.
enddate | no | string | The end date of the call timestamp to search for.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
total | number | Number of calls tracked during the summary period.
loanId | string | The loan identifier.
borrowerId | string | The borrower identifier.
phoneNumber | string | The phone number dialed.
callStatus | enum | Result of the call. Options: *Attempted, Contacted*. 
minCall | date | Earliest call tracked during the summary period.
maxCall | date | Last call tracked during the summary period.