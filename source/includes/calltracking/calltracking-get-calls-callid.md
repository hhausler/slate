<!--Endpoint introduction -->
## Get Call Summaries by Call ID

### GET /calltracking/calls/{callid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/calltrackingapi/calltracking/calls/6b9bc3a0-56e0-431f-8177-92a0192adeb2 \
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
var client = new RestClient("https://api.nelnet.io/calltrackingapi/calltracking/calls/6b9bc3a0-56e0-431f-8177-92a0192adeb2");
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

xhr.open("GET", "https://api.nelnet.io/calltrackingapi/calltracking/calls/6b9bc3a0-56e0-431f-8177-92a0192adeb2");
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

conn.request("GET", "calltrackingapi,calltracking,calls,6b9bc3a0-56e0-431f-8177-92a0192adeb2", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "callId": "6b9bc3a0-56e0-431f-8177-92a0192adeb2",
        "tenantId": 314,
        "servicerId": 2,
        "loanId": "7ff93bb1-6e6f-45ec-84d7-de0c48f7b659",
        "borrowerId": "9ffca9e7-b2db-478c-9f57-21ce45bf965a",
        "phoneNumber": "+13036963303",
        "callStatus": "Attempted",
        "callTimestamp": "2020-07-10T18:10:05.000Z",
        "createdBy": {
            "aud": "string",
            "exp": 1111111111,
            "iat": 1111111111,
            "iss": "string",
            "sub": "string",
            "email": "string",
            "groups": [
                "processor"
            ],
            "region": "string",
            "eventId": "string",
            "lenders": [
                "string",
                "string"
            ],
            "authTime": 1111111111,
            "clientId": "2",
            "tenantId": "314",
            "tokenUse": "id",
            "userName": "string",
            "borrowerId": null,
            "servicerId": "2",
            "userPoolId": "us-west-2_WHSE88shs",
            "phoneNumber": "string",
            "poolClientId": "string",
            "emailVerified": true,
            "phoneNumberVerified": true
        },
        "updatedBy": {
            "aud": "string",
            "exp": 1111111111,
            "iat": 1111111111,
            "iss": "string",
            "sub": "string",
            "email": "string",
            "groups": [
                "processor"
            ],
            "region": "string",
            "eventId": "string",
            "lenders": [
                "string",
                "string"
            ],
            "authTime": 1111111111,
            "clientId": "2",
            "tenantId": "314",
            "tokenUse": "id",
            "userName": "string",
            "borrowerId": null,
            "servicerId": "2",
            "userPoolId": "us-west-2_WHSE88shs",
            "phoneNumber": "string",
            "poolClientId": "string",
            "emailVerified": true,
            "phoneNumberVerified": true
        }
    }
}
```

<!-- LEFT: documentation -->

**Get call summaries based on loan, borrower, phone number, status, start date or end date.**

### HTTP Request

`GET https://api.nelnet.io/calltrackingapi/calltracking/calls/{callid}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
callid | yes | string | The ID of the call to retrieve.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
callId | string | The unique, GUID identifier for the call.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
loanId | string | The loan identifier.
borrowerId | string | The borrower identifier.
phoneNumber | string | The phone number dialed.
callStatus | enum | Result of the call. Options: *Attempted, Contacted*.
callTimestamp | date | The time that the call was made.
createdDate | date | The date that the records were created.
updatedDate | date | The date that the records last updated.
updatedBy | string | The Velocity user account that last updated records returned.
createdBy | string | The Velocity user account that created the records returned.