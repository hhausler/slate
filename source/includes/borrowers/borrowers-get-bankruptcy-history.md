<!--Endpoint introduction -->
## Get Bankruptcy Status History for a Borrower

### GET /borrowers/bankruptcy/history/{borrowerId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/borrowerapi/borrowers/bankruptcy/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/bankruptcy/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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

xhr.open("GET", "https://api.nelnet.io/borrowerapi/borrowers/bankruptcy/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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
conn.request("GET", "/borrowerapi/borrowers/bankruptcy/history/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "bankruptcyHistoryId": "d7f02341-00ee-411c-bdc4-910d5dc6dc2d",
        "tenantId": "314",
        "servicerId": "2",
        "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
        "bankruptcyType": "Chapter 7",
        "isActive": false,
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
        "createdDate": "2020-01-13T21:11:58.710Z"
    }
}
```

<!-- LEFT: documentation -->

**Returns a given borrower's bankruptcy status history.**

### HTTP Request

`GET https://api.nelnet.io/borrowerapi/borrowers/bankruptcy/history/{borrowerId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
borrowerId | yes | string (path parameter) | The identifier for the borrower to return.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
bankruptcyHistoryId | string | The identifier for the bankruptcy status.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
borrowerId | string | The identifier for the borrower.
bankruptcyType | enum | The type of bankruptcy filed by the borrower. Options: *Chapter 7*, *Chapter 13*.
isActive | boolean | Indicates whether the bankruptcy filing is active.
createdBy | string | The Velocity user account that created the records returned.
createdDate | date | The date that the record was created.