## Add or Update Custom Data for a Borrower

Use this endpoint to add or update custom data for a borrower, given the Borrower ID and the data to add to the borrower record.

<aside class="warning">
The posted data will be merged with the borrower’s existing custom data, overwriting the values of any matching keys and adding values for new keys.
</aside>

### POST /borrowers/{borrowerId}/customdata

<!--CODE EXAMPLES -->

> Sample request:

```shell
curl --request POST \
  --url https://api.nelnet.io/borrowerapi/borrowers/55f7b01e-a74d-49d2-9166-fb955dfdc379/customdata \
  --header 'Accept: */*' \
  --header 'Accept-Encoding: gzip, deflate' \
  --header 'Authorization: <ACCESS TOKEN>' \
  --header 'Cache-Control: no-cache' \
  --header 'Connection: keep-alive' \
  --header 'Content-Length: 80' \
  --header 'Content-Type: application/json' \
  --header 'Host: api.nelnet.io' \
  --header 'cache-control: no-cache' \
  --data '{\n    "BestNFLTeam": "Denver Broncos",\n    "BestNHLTeam": "Colorado Avalanche"\n}'
```
```csharp
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/55f7b01e-a74d-49d2-9166-fb955dfdc379/customdata");
var request = new RestRequest(Method.POST);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Content-Length", "80");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
request.AddParameter("undefined", "{\n    \"BestNFLTeam\": \"Denver Broncos\",\n    \"BestNHLTeam\": \"Colorado Avalanche\"\n}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```
```javascript
var data = JSON.stringify({
  "BestNFLTeam": "Denver Broncos",
  "BestNHLTeam": "Colorado Avalanche"
});

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("POST", "https://api.nelnet.io/borrowerapi/borrowers/55f7b01e-a74d-49d2-9166-fb955dfdc379/customdata");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Accept", "*/*");
xhr.setRequestHeader("Cache-Control", "no-cache");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("Accept-Encoding", "gzip, deflate");
xhr.setRequestHeader("Content-Length", "80");
xhr.setRequestHeader("Connection", "keep-alive");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);
```
```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

payload = "{\n    \"BestNFLTeam\": \"Denver Broncos\",\n    \"BestNHLTeam\": \"Colorado Avalanche\"\n}"

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Content-Type': "application/json",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Content-Length': "80",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("POST", "borrowerapi,borrowers,55f7b01e-a74d-49d2-9166-fb955dfdc379,customdata", payload, headers)

res = conn.getresponse()
data = res.read()
```
> JSON returned:

```json
{
  "data": {
    "borrowerId": "string",
    "tenantId": "string",
    "servicerId": "string",
    "firstName": "string",
    "middleName": "string",
    "lastName": "string",
    "suffix": "string",
    "ssn": "string",
    "dob": "string",
    "addresses": [
      {
        "street1": "string",
        "street2": "string",
        "city": "string",
        "state": "string",
        "postalCode": "string",
        "countryCode": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "addressesCreatedDate": "2019-11-15T21:08:34.012Z",
    "phoneNumbers": [
      {
        "phoneNumber": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "phoneNumbersCreatedDate": "2019-11-15T21:08:34.012Z",
    "emailAddresses": [
      {
        "emailAddress": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "emailAddressesCreatedDate": "2019-11-15T21:08:34.012Z",
    "customData": {
        "name1": "value1",
        "name2": "value2"
    },
    "activeMilitary": true,
    "activePrivacy": true,
    "activeBankruptcy": true,
    "activeDeath": true,
    "activeDisability": true,
    "createdDate": "2019-11-15T21:08:34.012Z",
    "updatedDate": "2019-11-15T21:08:34.012Z",
    "externalReferenceId": "string",
    "communicationPreferences": [
      {
        "eventType": "string",
        "communicationMethod": "sms",
        "communicationValue": "string"
      }
    ],
    "onboardingId": "string",
    "lenderId": "string",
    "ecorrAccepted": true,
    "createdBy": "string",
    "updatedBy": "string",
    "borrowerNumber": "string",
    "borrowerNumberFormatted": "string"
  }
}
```

<!--BODY TEXT -->

**Adds/updates custom data to a borrower record.**

`POST https://api.nelnet.io/borrowerapi/borrowers/{borrowerId}/customdata`

### HTTP Request

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
borrowerId | yes | string | The Borrower ID for the borrower record to be returned.
data | yes | object | The custom data to add to the borrower record, in the form of a key-value-pair JSON object.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response body.
borrowerId | string | The Borrower ID for the record being returned.
tenantId | string | The identifier for the tenant on which the borrower record is saved.
servicerId | string | The identifier for the servicer associated with the borrower record.
firstName | string | The borrower's first name.
middleName | string | The borrower's middle name.
lastName | string | The borrower's last name.
suffix | string | The borrower's name suffix (Jr., Sr., etc.).
ssn | string | The borrower's Social Security number.
dob | string | The borrower's date of birth.
addresses | object | An array containing the address(es) associated with the borrower.
addresses.street1 | string | The first line of the borrower's address.
addresses.street2 | string | The second line of the borrower's address.
addresses.city | string | City field for a borrower address.
addresses.postalCode | string | Postal code (ZIP code) field for a borrower's address.
addresses.countryCode | string | Country code field for a borrower's address.
addresses.isPrimary | boolean | Indicates whether the address has been flagged as the borrower's primary address. 
addresses.isValid | boolean | Indicates whether the address has been verified as the currently valid address for the borrower.
addressesCreatedDate | date | The date on which the address was added to the borrower record.
phoneNumbers | object | An array containing the phone number(s) associated with the borrower.
phoneNumbers.phoneNumber | string | The phone number for the borrower. 
phoneNumbers.isPrimary | boolean | Indicates whether the phone number has been flagged as the primary contact phone number for the borrower. 
phoneNumbers.isValid | boolean | Indicates whether the phone number has been verified as a currently valid phone number for the borrower.
phoneNumbersCreatedDate | date | The date on which the phone numbers were added to the borrower record.
emailAddresses | object | An array containing the email address(es) associated with the borrower. 
emailAddresses.emailAddress | string | The borrower's email address.
emailAddresses.isPrimary | boolean | Indicates whether the email address has been flagged as the primary contact email address for the borrower.
emailAddresses.isValid | boolean | Indicates whether the email address has been verified as a currently valid email address for the borrower.
emailAddressesCreatedDate | date | The date on which the email address was added to the borrower record. 
customData | object | The custom data associated with the borrower record. 
activeMilitary | boolean | Indicates whether the borrower record has the military servicemember flag.
activePrivacy | boolean | Indicates whether the borrower record has the privacy flag.
activeDeath | boolean | Indicates whether the borrower record has the death flag.
activeDisability | boolean | Indicates whether the borrower record has the disability flag.
createdDate | date | Date on which the borrower record was created.
updatedDate | date | Date of most recent update to the borrower record.
externalReferenceId | string | Unique identifier for the borrower record — can be set to anything, but must be unique. (Set as part of onboarding process.)
communicationPreferences | object | An array containing the borrower's communications preference data.
communicationPreferences. eventType | string | The communications event type.
communicationPreferences. communicationMethod | string | The borrower's preferred communication method (email, electronic correspondence, etc.).
communicationPreferences. communicationValue | string | The value of the communication sent.
onboardingId | string | The identifier for the onboarding bundle assigned when the borrower was added (via call to the Onboarding service) to Velocity.
lenderId | string | The identifier for the lender.
ecorrAccepted | boolean | Indicates whether the borrower has opted in to electronic correspondence.
createdBy | string | Name of the user (based on authorization token) that added the borrower to the system.
updatedBy | strong | Name of the user (based on authorization token) that last updated the borrower record.
borrowerNumber | string | GUID borrower identifier.
borrowerNumberFormatted | string | "Friendly" borrower ID.