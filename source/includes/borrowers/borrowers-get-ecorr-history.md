<!--Endpoint introduction -->
## Get Electronic Correspondence History for a Borrower

### GET /borrowers/ecorr/history/{borrowerId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/borrowerapi/borrowers/ecorr/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867 \
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
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/ecorr/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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

xhr.open("GET", "https://api.nelnet.io/borrowerapi/borrowers/ecorr/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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

conn.request("GET", "borrowerapi,borrowers,ecorr,history,0f5afdba-2e6d-4fe7-b4dd-9b25b018e867", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "ecorrHistoryId": "ac5724ce-c6a8-4bdc-bf76-cf13cb7424c6",
            "tenantId": "314",
            "servicerId": "2",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "ecorrAccepted": false,
            "createdBy": {
                "aud": "7lq6b7b3d1fhtclfmncjqdubqh",
                "exp": 1578413823,
                "iat": 1578410223,
                "iss": "https://cognito-idp.us-west-2.amazonaws.com/us-west-2_WHSE88shs",
                "sub": "fb1d7c8b-f8ad-4ab8-b734-b727ae8cd9a5",
                "email": "example@nelnet.net",
                "groups": [
                    "agent"
                ],
                "region": "us-west-2",
                "eventId": "63e472fd-0594-45a9-9bd7-0300b9eb6582",
                "lenders": [
                    "bbfc1a01-61d4-4556-afac-3f98b970e397",
                    "e6310976-06ab-4ddd-8d48-58683e94c246"
                ],
                "authTime": 1578410223,
                "clientId": "2",
                "tenantId": "314",
                "tokenUse": "id",
                "userName": "michaelagent",
                "borrowerId": null,
                "servicerId": "2",
                "userPoolId": "us-west-2_WHSE88shs",
                "phoneNumber": "+17154616478",
                "poolClientId": "7lq6b7b3d1fhtclfmncjqdubqh",
                "emailVerified": true,
                "phoneNumberVerified": true
            },
            "createdDate": "2020-01-07T15:20:35.871Z"
        },
        {
            "ecorrHistoryId": "1fdd03fb-79a9-448e-9b22-bdb6dc7ca72f",
            "tenantId": "314",
            "servicerId": "2",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "ecorrAccepted": false,
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
            "createdDate": "2019-12-12T15:19:33.308Z"
        }
    ]
}
```

<!-- LEFT: documentation -->

**Returns a borrower's electronic correspondence records.**

### HTTP Request

`GET https://api.nelnet.io/borrowerapi/borrowers/ecorr/history/{borrowerId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
borrowerId | yes | string (path parameter) | The identifier for the borrower. 

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
ecorrHistoryId | string | The identifier (GUID) for each electronic correspondence record returned.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
lenderId | string | The lender identifier.
borrowerId | string | The borrower identifier.
ecorrAccepted | boolean | Indicates whether the borrower has opted in for and accepted terms and conditions to receive all correspondence electronically rather than by mail.
createdBy | string | The Velocity user account that created the records returned.
createdDate | date | The date that the lender record was created.