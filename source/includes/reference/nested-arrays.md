## Borrower Information Arrays

Borrower Address Field | Notes | Type | Info
---------- | ------- | ------- | -------
street1 | yes | string | Street 1 field for a borrower address.
street2 | no | string | Street 2 field for a borrower address.
city | yes | string | City field for a borrower address.
state | yes | string | State field for a borrower address.
postalCode | yes | string | Postal code for a borrower address.
countryCode | yes | string | Country code for a borrower's address. Must be in ISO alpha-3 format.
isPrimary | yes | boolean | Indicates whether the address provided is the borrower's primary address. Defaults to *true*.

Borrower Phone Number Field | Notes | Type | Info
---------- | ------- | ------- | -------
phoneNumber | yes | string | Borrower's E.164 formatted phone number.
isPrimary | yes | boolean | Indicates whether the phone number provided is the borrower's primary phone number. Defaults to *true*.
isMobile | yes | boolean | Indicates whether the phone number provided is a cell phone/number for a mobile phone.
hasCellPhoneConsent | yes | boolean | Indicates whether the borrower has opted in for contact via cell phone.

Borrower Email Address Field | Notes | Type | Info
---------- | ------- | ------- | -------
emailAddress | yes | string | Borrower's email address.
isPrimary | yes | boolean | Indicates whether the email address provided is the borrower's primary email address.