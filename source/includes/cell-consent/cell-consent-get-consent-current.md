<!--Endpoint introduction -->
## Get Current Cell Phone Consent Information for a Borrower and Phone Number

### GET /cellphoneconsent/{borrowerid}/{phonenumber}/current

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568/current' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568/current");
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

xhr.open("GET", "https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568/current");
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
conn.request("GET", "/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568/current", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "cpcId": "a4fce66a-effb-402e-975b-9a0d7b221d0c",
        "tenantId": "314",
        "servicerId": "2",
        "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
        "phoneNumber": "+15551234568",
        "hasConsent": true,
        "createdDate": "2020-01-29T15:34:24.672Z",
        "createdBy": "Agent",
        "createdByToken": {}
    }
}
```

<!-- LEFT: documentation -->

**Returns the current cell phone consent information for a borrower's phone number.**

### HTTP Request

`GET https://api.nelnet.io/cellconsentapi/cellphoneconsent/{borrowerid}/{phonenumber}/current`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
borrowerid | yes | string | The identifier for the borrower.
phoneid | yes | string | The identifier for the phon number.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
cpcId | string | The identifer for the cell phone consent record.
tenantId | string | The identifer for the tenant.
servicerId | string | The identifer for the servicer.
borrowerId | string | The identifer for the borrower.
phoneNumber | string | The phone number associated with the cell phone consent record.
hasConsent | boolean | Indicates whether the phone number has cell phone consent.
createdDate | string | The date that the record was created.
createdBy | string | The user type for the account that created the record.
createdByToken | string | The user information for the account that created the record.