<!--Endpoint introduction -->
## Get Phone Number History for a Borrower

### GET /borrowers/{borrowerId}/phonenumbers

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/phonenumbers \
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
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/phonenumbers");
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

xhr.open("GET", "https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/phonenumbers");
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

conn.request("GET", "borrowerapi,borrowers,0f5afdba-2e6d-4fe7-b4dd-9b25b018e867,phonenumbers", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "phoneHistoryId": "508339d3-d966-46cc-8a1d-48a55d1cc0a8",
        "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
        "tenantId": "314",
        "servicerId": "2",
        "phoneNumbers": [
            {
                "phoneNumber": "+15551234568",
                "isPrimary": true,
                "isValid": true
            },
            {
                "phoneNumber": "+15552224322",
                "isPrimary": false,
                "isValid": false
            }
        ],
        "createdDate": "2020-01-29T15:34:24.293Z",
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
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns a given borrower's email addresses.**

### HTTP Request

`GET https://api.nelnet.io/borrowerapi/borrowers/{borrowerId}/phonenumbers`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
borrowerId | yes | string | The identifier for the borrower.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
emailaddressHistoryId | string | The identifier for the email address history associated with the borrower.
borrowerId | string | The identifier for the borrower.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
phonenumbers | object | The borrower's addresses.
phonenumbers.street1 | string | The street number and name for the address.
phonenumbers.street2 | string | The address second line.
phonenumbers.city | string | The address city.
phonenumbers.state | string | The address state.
phonenumbers.postalCode | string | The address postal or ZIP code.
phonenumbers.countryCode | string | The address country code.
phonenumbers.isPrimary | boolean | Indicates whether the address is the borrower's primary address.
phonenumbers.isValid | boolean | Indicates whether the address is confirmed as valid.
createdDate | date | The date that the address record was created.
createdBy | string | The user (associated token) who created the address record.