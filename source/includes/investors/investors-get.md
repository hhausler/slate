<!--Endpoint introduction -->
## Get Investors

### GET /investors

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/investorapi/investors?limit=2' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/investorapi/investors?limit=2");
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

xhr.open("GET", "https://api.nelnet.io/investorapi/investors?limit=2");
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
conn.request("GET", "/investorapi/investors?limit=2", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "investorId": "0125ae76-7aec-4d02-a40f-d7fb77392f14",
            "tenantId": "314",
            "servicerId": "2",
            "investorNumber": "10273",
            "lenderId": "7dc9b2b7-bc53-4e5c-8021-e797206e86c2",
            "name": "test test 112344555555578909900000",
            "identifierNumber": null,
            "externalReferenceId": null,
            "customData": null,
            "createdDate": "2020-04-17T19:38:34.728Z",
            "updatedDate": "2020-05-21T18:17:00.531Z",
            "addresses": [
                {
                    "countryCode": "USA",
                    "isMailing": true,
                    "isValid": true
                }
            ],
            "phoneNumbers": [
                {
                    "isPrimary": true,
                    "isValid": true
                }
            ],
            "bankAccountNumber": null,
            "bankRoutingNumber": null,
            "accountType": null,
            "createdBy": {},
            "updatedBy": {}
        },
        {
            "investorId": "01b6bdc9-b4d2-49eb-a9b6-7693dcfaccca",
            "tenantId": "314",
            "servicerId": "2",
            "investorNumber": "10095",
            "lenderId": "3824201a-1984-496f-a14b-774ce0884722",
            "name": "${name}",
            "identifierNumber": "123456789",
            "externalReferenceId": "72b43b35-7150-439a-b268-c21e6910fc27",
            "customData": null,
            "createdDate": "2019-06-17T15:04:08.445Z",
            "updatedDate": "2019-06-17T15:04:08.445Z",
            "addresses": [
                {
                    "street1": "5692 jupiter dr",
                    "street2": "5692 jupiter dr",
                    "city": "denver",
                    "state": "Co",
                    "postalCode": "80000",
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
            "bankAccountNumber": "12345678911",
            "bankRoutingNumber": "011102502",
            "accountType": "Checking",
            "createdBy": {},
            "updatedBy": {}
        }
    ],
    "paging": {
        "rows": 384,
        "pages": 192,
        "offset": 0,
        "limit": 2,
        "links": {
            "first": "/v1/investors?offset=0&limit=2",
            "last": "/v1/investors?offset=384&limit=2",
            "next": "/v1/investors?offset=2&limit=2"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns information on investors.**

### HTTP Request

`GET https://api.nelnet.io/investorapi/investors`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
lenderid | no | string | Identifier for a lender to narrow the investor records returned.
offset | no | number | The starting record in the return - the offset between the records returned and list of total records. Defaults to 0.
limit | no | number | The number of records per page. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
offset | number | The starting record in the return - the offset between the records returned and list of total records.
limit | number | The number of records per page.
links | object | Information about the pagination and links in the response.
first | string | A link to the first page of records returned.
last | string | A link to the last page of records returned.
previous | string | A link to the previous page in the list of records returned.
next | string | A link to the next page in the list of records returned.
data | object | The response payload.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
servicerId | string | The identifer for the servicer.
investorNumber | string | The "friendly ID" for the investor.
lenderId | string | The identifier for the lender.
name | string | The name of the lender.
identifierNumber | string | The identifier number for the lender.
addresses | object | An array containing the address(es) associated with the borrower.
addresses.street1 | string | The first line of the borrower's address.
addresses.street2 | string | The second line of the borrower's address.
addresses.city | string | City field for a borrower address.
addresses.postalCode | string | Postal code (ZIP code) field for a borrower's address.
addresses.countryCode | string | Country code field for a borrower's address.
addresses.isPrimary | boolean | Indicates whether the address has been flagged as the borrower's primary address. 
addresses.isValid | boolean | Indicates whether the address has been verified as the currently valid address for the borrower.
phoneNumbers | object | An array containing the phone number(s) associated with the borrower.
phoneNumbers.phoneNumber | string | The phone number for the borrower. 
phoneNumbers.isPrimary | boolean | Indicates whether the phone number has been flagged as the primary contact phone number for the borrower. 
phoneNumbers.isValid | boolean | Indicates whether the phone number has been verified as a currently valid phone number for the borrower.
bankAccountNumber | string | The investor's bank account number. Can be between 4 and 17 digits long.
bankRoutingNumber | string | The investor's bank routing number. Must be 9 digits long.
accountType | enum | Options: *Checking*, *Savings*.
externalReferenceId | string | An external reference ID for the investor.
customData | object | Any custom data added to the investor record.
createdDate | date | Date on which the record was created.
updatedDate | date | Date of latest update.
createdBy | object | Information about the user who created the investor record.
updatedBy | object | Information about the user who updated the investor record.