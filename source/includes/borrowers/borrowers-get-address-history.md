<!--Endpoint introduction -->
## Get Address History for a Borrower

### GET /borrowers/{borrowerId}/addresses

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/addresses \
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
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/addresses");
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

xhr.open("GET", "https://api.nelnet.io/borrowerapi/borrowers/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/addresses");
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

conn.request("GET", "borrowerapi,borrowers,0f5afdba-2e6d-4fe7-b4dd-9b25b018e867,addresses", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "addressHistoryId": "9cc07353-30f0-4f4a-b152-665c043b2132",
        "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
        "tenantId": "314",
        "servicerId": "2",
        "addresses": [
            {
                "street1": "134 Razor Crest",
                "street2": null,
                "city": "Eau Claire",
                "state": "WI",
                "postalCode": "54703",
                "countryCode": "USA",
                "isPrimary": true,
                "isValid": true
            },
            {
                "street1": "5694 Jupiter Dr",
                "street2": "",
                "city": "Mason",
                "state": "FL",
                "postalCode": "23587",
                "countryCode": "USA",
                "isPrimary": false,
                "isValid": true
            }
        ],
        "createdDate": "2020-03-20T18:35:28.234Z",
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

**Returns a given borrower's addresses.**

### HTTP Request

`GET https://api.nelnet.io/borrowerapi/borrowers/{borrowerId}/addresses`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
borrowerId | yes | string | The identifier for the borrower.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
addressHistoryId | string | The identifier for the address history associated with the borrower.
borrowerId | string | The identifier for the borrower.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
addresses | object | The borrower's current addresses.
addresses.street1 | string | The street number and name for the address.
addresses.street2 | string | The address second line.
addresses.city | string | The address city.
addresses.state | string | The address state.
addresses.postalCode | string | The address postal or ZIP code.
addresses.countryCode | string | The address country code.
addresses.isPrimary | boolean | Indicates whether the address is the borrower's primary address.
addresses.isValid | boolean | Indicates whether the address is confirmed as valid.
createdDate | date | The date that the address record was created.
createdBy | string | The user (associated token) who created the address record.