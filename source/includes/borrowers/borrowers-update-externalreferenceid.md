## Update Borrower's External Reference ID

### PUT /borrowers/externalreferenceid/{borrowerId}

<!--CODE EXAMPLES -->

> Sample request:

```shell
curl --location --request PUT 'https://api.nelnet.io/borrowerapi/borrowers/externalreferenceid/00000000-0000-0000-0000-000000000000' \
--header 'Content-Type: application/json' \
--header 'Authorization: <ACCESSTOKEN>' \
--data-raw '{
  "externalReferenceId": "New External Reference ID String or NULL"
}'
```

```csharp
var client = new RestClient("https://api.nelnet.io/borrowerapi/borrowers/externalreferenceid/00000000-0000-0000-0000-000000000000");
client.Timeout = -1;
var request = new RestRequest(Method.PUT);
request.AddHeader("Content-Type", "application/json");
request.AddHeader("Authorization", "<ACCESSTOKEN>");
request.AddParameter("application/json", "{\n  \"externalReferenceId\": \"New External Reference ID String or NULL\"\n}",  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

```javascript
var data = JSON.stringify({"externalReferenceId":"New External Reference ID String or NULL"});
 
var xhr = new XMLHttpRequest();
xhr.withCredentials = true;
 
xhr.addEventListener("readystatechange", function() {
  if(this.readyState === 4) {
    console.log(this.responseText);
  }
});
 
xhr.open("PUT", "https://api.nelnet.io/borrowerapi/borrowers/externalreferenceid/00000000-0000-0000-0000-000000000000");
xhr.setRequestHeader("Content-Type", "application/json");
xhr.setRequestHeader("Authorization", "<ACCESSTOKEN>");
 
xhr.send(data);
```

```python
import http.client
import mimetypes
conn = http.client.HTTPSConnection("api.nelnet.io")
payload = "{\n  \"externalReferenceId\": \"New External Reference ID String or NULL\"\n}"
headers = {
  'Content-Type': 'application/json',
  'Authorization': '<ACCESSTOKEN>'
}
conn.request("PUT", "/borrowerapi/borrowers/externalreferenceid/00000000-0000-0000-0000-000000000000", payload, headers)
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
    "addressesCreatedDate": "2020-03-09T17:06:52.497Z",
    "phoneNumbers": [
      {
        "phoneNumber": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "phoneNumbersCreatedDate": "2020-03-09T17:06:52.497Z",
    "emailAddresses": [
      {
        "emailAddress": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "emailAddressesCreatedDate": "2020-03-09T17:06:52.497Z",
    "customData": {},
    "activeMilitary": true,
    "activePrivacy": true,
    "activeBankruptcy": true,
    "activeDeath": true,
    "activeDisability": true,
    "createdDate": "2020-03-09T17:06:52.497Z",
    "updatedDate": "2020-03-09T17:06:52.497Z",
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

**Update an external reference ID for an existing borrower.**

Call this endpoint to add or replace a borrower's external reference ID.

`GET https://api.nelnet.io/borrowerapi/borrowers/{borrowerId}`

### HTTP Request

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
borrowerId | yes | string | The identifier for the borrower to update. (Path parameter.)
externalReferenceId | yes | string | The updated external reference ID. (Body parameter.)

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