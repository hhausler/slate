<!--Endpoint introduction -->
## Get Cell Phone Consent Information for a Borrower

### GET /cellphoneconsent/{borrowerid}/{phonenumber}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568");
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

xhr.open("GET", "https://api.nelnet.io/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568");
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
conn.request("GET", "/cellconsentapi/cellphoneconsent/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "cpcId": "7b74e870-0e8e-4677-b990-c1c3125b9099",
            "tenantId": "314",
            "servicerId": "2",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "phoneNumber": "+15551234568",
            "hasConsent": true,
            "createdDate": "2020-01-07T15:20:39.130Z",
            "createdBy": "Agent",
            "createdByToken": {}
        },
        {
            "cpcId": "14f2badb-2467-4bbd-8637-cb84af4e7b78",
            "tenantId": "314",
            "servicerId": "2",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "phoneNumber": "+15551234568",
            "hasConsent": false,
            "createdDate": "2019-12-12T15:19:35.205Z",
            "createdBy": "Agent",
            "createdByToken": {}
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 20,
        "total": 18,
        "pageCount": 1,
        "links": {
            "first": "/cpc/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568?offset=0&limit=20",
            "last": "/cpc/0f5afdba-2e6d-4fe7-b4dd-9b25b018e867/+15551234568?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns cell phone consent history for a borrower's phone number.**

### HTTP Request

`GET https://api.nelnet.io/cellconsentapi/cellphoneconsent/{borrowerid}/{phonenumber}`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
borrowerid | yes | string | 
phoneid | yes | string |

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
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