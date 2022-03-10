## Get Borrower Records

Use this endpoint to get the data saved as a borrower for all borrower records

### GET /borrowers

<!--CODE EXAMPLES -->

> Sample request:

```shell
```
```csharp
```
```javascript
```
```python

```
> JSON returned:

```json
{
  "paging": {
  "rows": 0,
  "pages": 0,
  "offset": 0,
  "limit": 0,
  "links": {
    "first": "string",
    "last": "string",
    "previous": "string",
    "next": "string"
  }
},
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
    "addressesCreatedDate": "2019-11-15T21:01:35.638Z",
    "phoneNumbers": [
      {
        "phoneNumber": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "phoneNumbersCreatedDate": "2019-11-15T21:01:35.638Z",
    "emailAddresses": [
      {
        "emailAddress": "string",
        "isPrimary": true,
        "isValid": true
      }
    ],
    "emailAddressesCreatedDate": "2019-11-15T21:01:35.638Z",
    "customData": {
        "name1": "value1",
        "name2": "value2"
    },
    "activeMilitary": true,
    "activePrivacy": true,
    "activeBankruptcy": true,
    "activeDeath": true,
    "activeDisability": true,
    "createdDate": "2019-11-15T21:01:35.638Z",
    "updatedDate": "2019-11-15T21:01:35.638Z",
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

**Returns a full borrower record for all borrowers.**

`GET https://api.nelnet.io/borrowerapi/borrowers`

### HTTP Request

Parameter | Required | Type | Description
---------- | ------- | ------- | -------
ssn | no | string | The social security number of the borrower.
dob | no | string | The borrower date of birth.
externalreferenceId | no | string | The external reference ID for the borrower.
phonenumber | no | string | The phone number for the borrower.
borrowernumber | no | string | The borrower number.
firstname | no | string | The first name of the borrower.
lastname | no | string | The last name of the borrower.
emailaddress | no | string | The borrower email address.
offset | no | number | The paging offset. Default value: 0.
limit | no | string | The paging limit. Default value: 20.


### HTTP Response

The response object `PagedResponseBodyBorrower` contains two large objects, `paging` and `data`.

**Paging Object**

Field Name | Type | Description
---------- | ------- | -------
rows | number($double) | The number of rows per page.
pages | number($double) | The number of pages.
offset | number($double) | The paging offset.
limit | number($double) | The paging limit.
links | object | Links to the paginate through the results set.
links.first | string | A link to the first record in the results set.
links.last | string | A link to the last record in the results set.
links.previous | string | A link to the previous record in the results set.
links.next | string | A link to the next record in the results set.

**Data.Loan Object**

The response object `data` contains the object `loan`, which contains the following.

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
customData | object | Any custom fields added to the borrower record.
activeMilitary | boolean | Indicates whether the borrower record has the military servicemember flag.
activePrivacy | boolean | Indicates whether the borrower record has the privacy flag.
activeDeath | boolean | Indicates whether the borrower record has the death flag.
activeDisability | boolean | Indicates whether the borrower record has the disability flag.
createdDate | date | Date on which the borrower record was created.
updatedDate | date | Date of most recent update to the borrower record.
externalReferenceId | string | Unique identifier for the borrower record — can be set to anything, but must be unique. (Set as part of onboarding process.)
communicationPreferences | object | An array containing the borrower's communications preference data.
communicationPreferences. eventType | string | Communications event type
communicationPreferences. communicationMethod | string | Preferred communication method (email, electronic correspondence, etc.)
communicationPreferences. communicationValue | string | Value of communication sent.
onboardingId | string | The identifier for the onboarding bundle assigned when the borrower was added (via call to the Onboarding service) to Velocity.
lenderId | string | The identifier for the lender
ecorrAccepted | boolean | Indicates whether the borrower has opted in to electronic correspondence.
createdBy | string | Name of the user (based on authorization token) that added the borrower to the system.
updatedBy | strong | Name of the user (based on authorization token) that last updated the borrower record.
borrowerNumber | string | GUID borrower identifier.
borrowerNumberFormatted | string | "Friendly" borrower ID.
