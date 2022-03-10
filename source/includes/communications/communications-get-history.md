<!--Endpoint introduction -->
## Get Communications Suppression History

### GET /communications/suppression/history/{loanId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: Bearer <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("tenantid", "314");
request.AddHeader("servicerid", "2");
request.AddHeader("Authorization", "Bearer <ACCESS TOKEN>");
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

xhr.open("GET", "https://api.nelnet.io/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "Bearer <ACCESS TOKEN>");

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
  'Authorization': 'Bearer <ACCESS TOKEN>'
}
conn.request("GET", "/communicationsapi/communications/suppression/latest/c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.de
```

> JSON returned:

```json
{
    "data": {
        "communicationSuppressionId": "29eecbb8-58b7-4baa-aa5b-d6c7adf29237",
        "tenantId": "314",
        "servicerId": "2",
        "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
        "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
        "isSuppressed": false,
        "suppressionType": null,
        "communicationType": null,
        "createdDate": "2020-08-06T12:59:24.680Z",
        "createdBy": {}
    }
}
```

<!-- LEFT: documentation -->

**Returns the communication suppression history for a loan.**

### HTTP Request

`GET https://api.nelnet.io/communicationsapi/communications/suppression/history/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan to return records for.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

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
communicationSuppressionId | string | The identifier for the communications suppression.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the communications suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether communicationss are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.
