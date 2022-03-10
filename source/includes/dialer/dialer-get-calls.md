<!--Endpoint introduction -->
## Get Dialer Calls

### GET /dialer/calls

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  'https://api.nelnet.io/dialerapi/dialer/calls?limit=1' \
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
var client = new RestClient("https://api.nelnet.io/dialerapi/dialer/calls?limit=1");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("User-Agent", "PostmanRuntime/7.18.0");
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

xhr.open("GET", "https://api.nelnet.io/dialerapi/dialer/calls?limit=1");
xhr.setRequestHeader("tenantid", "314");
xhr.setRequestHeader("servicerid", "2");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("User-Agent", "PostmanRuntime/7.18.0");
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

conn.request("GET", "dialerapi,dialer,calls", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "callCode": "DD-001",
            "lenderId": "e6310976-06ab-4ddd-8d48-58683e94c246",
            "lenderName": "Example Lender",
            "lenderShortName": "Example Lender",
            "lenderIdentifierNumber": "",
            "loanId": "22820c48-72fa-420f-b08a-aac68529d599",
            "loanNumber": "672182867011",
            "loanExternalReferenceId": "",
            "loanStatus": "repayment",
            "loanDaysLate": 62,
            "loanPaidToDate": "2020-06-02",
            "loanNextDueDate": "2020-08-11",
            "loanLastPaymentDate": null,
            "loanPastAmountDue": 425,
            "loanFeeOutstanding": 30,
            "loanInterestBalance": 109.65,
            "loanCurrentAmountDue": 85,
            "borrowerId": "7bc63907-babd-45e6-84cf-a4301d8c53f2",
            "borrowerNumber": "6336189931",
            "borrowerExternalReferenceId": "5619ceb9-82a2-4ab6-8004-a5e77eabf083",
            "borrowerType": "borrower",
            "borrowerFirstName": "Henry",
            "borrowerMiddleName": "A",
            "borrowerLastName": "Hudson",
            "borrowerSuffix": null,
            "borrowerPhoneNumber": "+13036963303",
            "borrowerCellPhoneConsent": false,
            "callAttemptsPerBucket": 4,
            "callContactsPerBucket": 1,
            "callDaysStart": 60,
            "callDaysEnd": 74,
            "callsAttempted": 0,
            "callsAttemptedMinDate": null,
            "callsAttemptedMaxDate": null,
            "callsContacted": 0,
            "callsContactedMinDate": null,
            "callsContactedMaxDate": null,
            "callId": "a8246bd7-4d33-4b9f-9a47-9decff83d1aa",
            "tenantId": 314,
            "servicerId": 2,
            "createdBy": {},
            "createdDate": "2020-08-03T09:42:53.795Z",
            "updatedBy": {},
            "updatedDate": "2020-08-03T09:42:53.795Z"
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 1,
        "links": {
            "first": "/calls?offset=0&limit=1",
            "last": "/calls?offset=71777&limit=1",
            "next": "/calls?offset=1&limit=1"
        }
    }
}

```

<!-- LEFT: documentation -->

**Returns dialer calls by date, loan, borrower, call code or phone number.**

### HTTP Request

`GET https://api.nelnet.io/dialerapi/dialer/calls`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
createddate | no | string | The created date of the records to return.
loanid | no | string | The loan ID of the records to return.
borrowerid | no | string | The borrower ID of the records to return.
callcode | no | string | The call code of the records to return.
phonenumber | no | string | The phone number of the records to return.
offset | no | number | string | The starting record in the return - the offset between the records returned and list of total records. Defaults to 0.
limit | no | number | string | The number of records per page. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
offset | number | The starting record in the return - the offset between the records returned and list of total records.
limit | number | The number of records per page.
links | object | Information about the pagination and links in the response.
links.first | string | A link to the first page of records returned.
links.last | string | A link to the last page of records returned.
links.previous | string | A link to the previous page in the list of records returned.
links.next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following is contained within `data`.
createdDate | string | The date that the records last updated.
updatedDate | string | The date that the records were created.
updatedBy | string | The Velocity user account that made the latest update to the records returned.
createdBy | string | The Velocity user account that created the dialer records returned.
callId | string | Unique GUID identifier for the call.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
callCode | string | Defined call code describing the type of call (delinquency, call campaign, etc.).
lenderId | string | The identifier for the lender.
lenderName | string | Name of the lender.
lenderShortName | string | The short name assigned to the lender.
lenderIdentifierNumber | string | The identifier number assigned to the lender.
loanId | string | The GUID identifier for the loan within Velocity.
loanNumber | string | The "friendly ID" for the loan within Velocity.
loanExternalReferenceId | string | External reference ID assigned to the loan.
loanStatus | string | The current loan status. Options: *charge off, default, forbearance, fraud, paid in full, rejected, repayment, write off.*
loanDaysLate | number | The number of days late, if any. 
loanPaidToDate | string | The actual next due date (representing how behind or how far ahead the loan is).
loanNextDueDate | string | The current billing cycle’s due date.
loanLastPaymentDate | string | Most recent payment date.
loanPastAmountDue | number | Past-due amount on the next due date.
loanFeeOutstanding | number | Outstanding fees due.
loanInterestBalance | number | Outstanding interest due.
loanCurrentAmountDue | number | Current amount due in this cycle.
borrowerId | string | The identifier (within Velocity) for the borrower.
borrowerNumber | string | The "friendly ID" for the borrower within Velocity (not the GUID).
borrowerExternalReferenceId | string | The external identifier for a borrower, such as the ID from the loan origination system.
borrowerType | string | Type of borrower. Options: *borrower, co-borrower.*
borrowerFirstName | string | The borrower's first name.
borrowerMiddleName | string | The borrower's middle name.
borrowerLastName | string | The borrower's last name.
borrowerSuffix | string | The borrower's name suffix.
borrowerPhoneNumber | string | The borrower's phone number.
borrowerCellPhoneConsent | boolean | Indicates whether the borrower has opted in for contact via cell phone.
callAttemptsPerBucket | number | Buckets are a range of days past due as defined by the loan program settings. Attempts are the number of call attempts allowed within that timeframe. Example: *For loans that are 1-15 days past due (bucket), make 4 call attempts (attempts) and stop after 1 contact is made (contacts).*
callContactsPerBucket | number | See `callAttemptsPerBucket`.
callDaysStart | number | Starting number of days past due for the bucket.
callDaysEnd | number | Ending number of days past due for the bucket.
callsAttempted | number | Number of attempts made within this bucket based on call-tracking information.
callsAttemptedMinDate | string | Bucket start date for the attempts.
callsAttemptedMaxDate | string | Projected bucket end date for attempts.
callsContacted | number | Number of contacts made within this bucket based on call tracking information.
callsContactedMinDate | string | Bucket start date for contacts (should match attempts).
callsContactedMaxDate | string | Projected bucket end date for contacts (should match attempts).