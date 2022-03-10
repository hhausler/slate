<!--Endpoint introduction -->
## Get Communication Settings for a Loan Program

### GET /loanprograms/{id}/communicationsettings

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanprogramapi/loanprograms/0038ac8d-1f1a-4c25-b056-96b7e841cb45/communicationsettings' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanprogramapi/loanprograms/0038ac8d-1f1a-4c25-b056-96b7e841cb45/communicationsettings");
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

xhr.open("GET", "https://api.nelnet.io/loanprogramapi/loanprograms/0038ac8d-1f1a-4c25-b056-96b7e841cb45/communicationsettings");
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
conn.request("GET", "/loanprogramapi/loanprograms/0038ac8d-1f1a-4c25-b056-96b7e841cb45/communicationsettings", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "communicationSettingId": "1d123b18-7992-4b02-9e83-597e02809020",
            "loanProgramId": "0038ac8d-1f1a-4c25-b056-96b7e841cb45",
            "tenantId": "314",
            "servicerId": "2",
            "code": "Dev Document Code",
            "name": "CLSample_Statement__VSCLINT73_Test",
            "type": "letter",
            "event": "QUASAR.STATEMENT.CREATED",
            "provider": "Inspire",
            "dataBlocks": [
                {
                    "dataBlock": "borrowerDetails"
                },
                {
                    "dataBlock": "loanDetails"
                },
                {
                    "dataBlock": "statementDetails"
                },
                {
                    "dataBlock": "autoDebitDetails"
                },
                {
                    "dataBlock": "callTrackingSummary"
                },
                {
                    "dataBlock": "paymentDetails"
                },
                {
                    "dataBlock": "currentDelinquencyDialerBucket"
                }
            ],
            "parameters": {
                "Another_Test": "false",
                "Test_Parameter": "false",
                "Testing_Params": "true"
            },
            "suppressionTags": [
                "none"
            ],
            "createdDate": "2020-06-03T20:26:17.097Z",
            "updatedDate": "2020-08-08T23:24:09.521Z",
            "isActive": true,
            "createdBy": {},
            "updatedBy": {}
        }
        {
            "communicationSettingId": "b9fddf2e-8921-4604-bbae-32f928ece8c6",
            "loanProgramId": "0038ac8d-1f1a-4c25-b056-96b7e841cb45",
            "tenantId": "314",
            "servicerId": "2",
            "code": "Dev Document",
            "name": "CLSample_Statement__VSCLINT73",
            "type": "letter",
            "event": "QUASAR.STATEMENT.CREATED",
            "provider": "Inspire-Test",
            "dataBlocks": [
                {
                    "dataBlock": "borrowerDetails"
                },
                {
                    "dataBlock": "loanDetails"
                },
                {
                    "dataBlock": "statementDetails"
                },
                {
                    "dataBlock": "autoDebitDetails"
                },
                {
                    "dataBlock": "callTrackingSummary"
                },
                {
                    "dataBlock": "paymentDetails"
                }
            ],
            "parameters": {
                "Another_Test": "false",
                "Test_Parameter": "false",
                "Testing_Params": "true"
            },
            "suppressionTags": [
                "none"
            ],
            "createdDate": "2020-02-24T18:16:23.620Z",
            "updatedDate": "2020-06-10T21:25:56.437Z",
            "isActive": true,
            "createdBy": {},
            "updatedBy": {}
        }
    ],
    "paging": {
        "rows": 3,
        "pages": 1,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/loanprograms/{id}/communicationsettings?offset=0&limit=20",
            "last": "/loanprograms/{id}/communicationsettings?offset=0&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns the communications settings for a loan program.**

### HTTP Request

`GET https://api.nelnet.io/loanprogramapi/loanprograms/{id}/communicationsetting`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
id | yes | string (path parameter) | The identifier for the loan program.
event | no | string | The event that triggers the communication.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
paging.offset | number ($double) | The starting record in the return - the offset between the records returned and list of total records.
paging.limit | number ($double) | The number of records per page.
paging.links | object | Information about the pagination and links in the response.
paging.links.first | string | A link to the first page of records returned.
paging.links.last | string | A link to the last page of records returned.
paging.links.previous | string | A link to the previous page in the list of records returned.
paging.links.next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following fields exist within `data`.
communicationSettingId | string | The identifer for the communication settings record.
loanProgramId | string | The identifer for the loan program.
tenantId | string | The identifier for the tenant.
code | string | The communication code.
name | string | The communication name.
type | enum | The communication type. Options: *call*, *email*, *letter*.
event | string | The communication trigger.
provider | string | The communication integration name.
dataBlocks | object | Information about the communication.
dataBlocks.dataBlock | string | The communication.
parameters | object | Parameters for settings on the communication.
suppressionTags | string | Tags on the communication for suppression purposes (used for suppressing all communications tagged *delinquency*).
isActive | boolean | Indicates whether the communication is active.
createdDate | date | The date that the record was created.
updatedDate | date | The latest date that the record was last updated.
createdBy | object | Information about the account that created the record.
updatedBy | object | Information about the account that last updated the record.
