<!--Endpoint introduction -->
## Get Lender by Lender ID

### GET /lenders/{lenderId}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/lenderapi/lenders/?lenderid=e6310976-06ab-4ddd-8d48-58683e94c246' \
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
var client = new RestClient("https://api.nelnet.io/lenderapi/lenders/?lenderid=e6310976-06ab-4ddd-8d48-58683e94c246");
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

xhr.open("GET", "https://api.nelnet.io/lenderapi/lenders/?lenderid=e6310976-06ab-4ddd-8d48-58683e94c246");
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

conn.request("GET", "lenderapi,lenders,", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "lenderId": "00b9ca6d-b11c-4d11-bbf7-706616e329a2",
            "tenantId": "314",
            "servicerId": "2",
            "name": "test_VSCLINT73_PUT",
            "shortName": "VSCLINT73_PUT",
            "creditReportIdentificationNumber": "123513252135",
            "addresses": [
                {
                    "street1": "8740 Lucent Blvd # 400",
                    "street2": "8740 Lucent Blvd # 400",
                    "city": "Highlands Ranch",
                    "state": "CO",
                    "postalCode": "80129",
                    "countryCode": "USA",
                    "isMailing": true,
                    "isValid": true
                }
            ],
            "phoneNumbers": [
                {
                    "phoneNumber": "+13036963303",
                    "isPrimary": true,
                    "isValid": true
                }
            ],
            "lenderNumber": "24028",
            "contactName": "VSCLINT73_PUT",
            "bankAccountNumber": "12345678911",
            "bankRoutingNumber": "011102502",
            "websiteUrl": "www.nelnet.VSCLINT73_PUT.net",
            "ecoaAgencyId": null,
            "callCenterHours": null,
            "emailAddress": null,
            "customData": null,
            "createdDate": "2020-01-15T17:11:13.634Z",
            "updatedDate": "2020-06-23T20:33:11.139Z",
            "createdBy": { },
            "updatedBy": {}
        }
    ],
    "paging": {
        "rows": 913,
        "pages": 46,
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/v1/lenders?offset=0&limit=20",
            "last": "/v1/lenders?offset=900&limit=20",
            "next": "/v1/lenders?offset=20&limit=20"
        }
    }
}
```

<!-- LEFT: documentation -->

**Gets a lender based on the lender ID.**

### HTTP Request

`GET https://api.nelnet.io/lenderapi/lenders/{lenderId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
lenderId | yes | string | The ID of the lender to retrieve.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
lenderId | string | The lender identifier.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
lenderNumber | string | The "friendly ID" for the lender.
name | string | The name of the lender.
creditReportIdentificationNumber | string | An identifier that allows the lender to report to credit bureaus.
bankAccountNumber | string | The lender's bank account number. Can be between 4 and 17 digits long.
bankRoutingNumber | string | The lender's bank routing number. Must be 9 digits long.
shortName | string | The lender's short name within Velocity.
contactName | string | The lender's contact name.
addresses | object | Information about the address or addresses for the lender.
addresses.street1 | string | Street address.
addresses.street2 | string | Street address second line, if used.
addresses.city | string | City.
addresses.state | string | State.
addresses.postalCode | string | Postal or ZIP code.
addresses.countryCode | string | Country code.
addresses.isMailing | boolean | Indicates whether the address is a mailing address.
addresses.isValid | boolean | Indicates whether the address has been verified as valid.
addressType | enum | Options: *Correspondence*, *Lockbox*.
phoneNumbers | object | Information about the phone number(s) for the lender.
phoneNumbers.phoneNumber | string | The lender's phone number.
phoneNumbers.isPrimary | boolean | Indicates whether this is the primary phone number for the lender.
phoneNumbers.isValid | boolean | Indicates whether the phone number has been verified as valid.
websiteUrl | string | Web address for the lender.
ecoaAgencyId | string | ECOA identifier for the lender.
callCenterHours | string | Hours that the call center is available.
emailAddress | string | The lender's email address.
customData | string | Any custom data saved as part of the lender record.
createdDate | date | The date that the lender record was created.
updatedDate | date | The date that the lender record was last updated.
createdBy | string | The Velocity user account that created the records returned.
updatedBy | string | The Velocity user account that last updated the records returned.