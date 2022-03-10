<!--Endpoint introduction -->
## Get Bank Profiles for a Borrower

### GET /bankprofiles

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/borrowerapi/bankprofiles?borrowerid=0f5afdba-2e6d-4fe7-b4dd-9b25b018e867' \
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
var client = new RestClient("https://api.nelnet.io/borrowerapi/bankprofiles?borrowerid=0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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

xhr.open("GET", "https://api.nelnet.io/borrowerapi/bankprofiles?borrowerid=0f5afdba-2e6d-4fe7-b4dd-9b25b018e867");
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

conn.request("GET", "borrowerapi,bankprofiles", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "bankProfileId": "d80c1922-88b7-4c7a-b31e-ff6886403d66",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "tenantId": "314",
            "servicerId": "2",
            "bankProfileName": "correct",
            "routingNumber": "011000028",
            "accountNumber": "852147963",
            "accountType": "Checking",
            "accountHolderFirstName": "den",
            "accountHolderLastName": "journ",
            "createdDate": "2020-01-23T22:14:54.180Z",
            "updatedDate": "2020-01-23T22:14:54.180Z",
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
            "updatedBy": {
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
        },
        {
            "bankProfileId": "ef700145-55ab-4d61-96d3-55e5e4b2635e",
            "borrowerId": "0f5afdba-2e6d-4fe7-b4dd-9b25b018e867",
            "tenantId": "314",
            "servicerId": "2",
            "bankProfileName": "profile",
            "routingNumber": "011000028",
            "accountNumber": "452365",
            "accountType": "Checking",
            "accountHolderFirstName": "profile",
            "accountHolderLastName": "test",
            "createdDate": "2019-11-05T19:51:54.521Z",
            "updatedDate": "2019-11-05T19:51:54.521Z",
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
            "updatedBy": {
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
    ]
}
```

<!-- LEFT: documentation -->

**Returns a list of all bank profiles for a given borrower.**

### HTTP Request

`GET https://api.nelnet.io/borrowerapi/bankprofiles`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
borrowerid | yes | string | The identifier for the borrower.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
bankProfileId | string | The identifier for the bank profile.
borrowerId | string | The identifier (within Velocity) for the borrower.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
bankProfileName | string | Name of the bank profile created.
routingNumber | string | The 9-digit routing number for the account saved in the profile.
accountNumber | string | The account number saved in the bank profile. Can be between 4 and 17 digits long.
accountType | enum | The account type. Options: *Checking, savings*.
accountHolderFirstName | string | The account holder's first name.
accountHolderLastName | string | The account holder's last name.
createdDate | date | The date that the bank profile was created.
updatedDate | date | The date that the bank profile was last updated.
createdBy | string | The Velocity user account that created the records returned.
updatedBy | string | The Velocity user account that last updated the records returned.