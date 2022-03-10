<!--Endpoint introduction -->
## Get Suppression Settings for a Loan

### GET /suppression/{loanid}

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/suppressionapi/suppression/c2d6aa46-ab71-475d-943a-dec948f99843 \
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
var client = new RestClient("https://api.nelnet.io/suppressionapi/suppression/c2d6aa46-ab71-475d-943a-dec948f99843");
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

xhr.open("GET", "https://api.nelnet.io/suppressionapi/suppression/c2d6aa46-ab71-475d-943a-dec948f99843");
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

conn.request("GET", "suppressionapi,suppression,c2d6aa46-ab71-475d-943a-dec948f99843", payload, headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": {
        "autodebit": {
            "isConfigured": true,
            "isSuppressed": false,
            "config": {
                "autoDebitId": "3ae7c909-ce05-4bea-9a0d-87e88cbc8ef7",
                "tenantId": "314",
                "servicerId": "2",
                "borrowerId": "7f471f43-e4fc-458a-b5f6-037bd5b10a2b",
                "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
                "routingNumber": "091000022",
                "accountNumber": "123456782",
                "accountType": "Checking",
                "accountHolderFirstName": "Alex",
                "accountHolderLastName": "Summers",
                "isActive": true,
                "onboardingId": "e3a22729-6a74-4465-be13-fa5f3e6983a1",
                "terms": {
                    "type": "HTML",
                    "content": "string"
                },
                "customAmount": null,
                "reason": null,
                "createdDate": "2020-07-23T19:43:54.156Z",
                "updatedDate": "2020-07-23T19:43:54.156Z",
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
                },
        "notifications": {
            "isEmailSuppressed": false,
            "isSmsSuppressed": false,
            "isVoiceSuppressed": false,
            "isWebhookSuppressed": false
        },
        "payments": {
            "isAchSuppressed": false,
            "isManualSuppressed": false
        },
        "isCollectionCallsSuppressed": false,
        "isCollectionLettersSuppressed": false,
        "isCommunicationsSuppressed": false,
        "isCreditReportingSuppressed": false,
        "isFeesSuppressed": false,
        "isPaymentDueSuppressed": false,
        "isStatementsSuppressed": false,
        "isAllSuppressed": false,
        "loan": {
            "loanId": "c2d6aa46-ab71-475d-943a-dec948f99843",
            "borrowers": [
                {
                    "borrowerId": "7f471f43-e4fc-458a-b5f6-037bd5b10a2b",
                    "borrowerType": "borrower"
                }
            ],
            "loanProgramId": "4646e4f5-4e33-4ef5-a6eb-a500523d6a49",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "status": "forbearance",
            "isBankruptcyActive": false,
            "isDeathActive": false,
            "isDisabilityActive": false,
            "isScraActive": false,
            "servicingStatus": "active",
            "effectiveDate": "2020-08-04"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns suppression settings for a given loan.**

### HTTP Request

`GET https://api.nelnet.io/suppressionapi/suppression/{loanid}`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
loanid | yes | string | The identifer for the loan to return suppression settings for.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
autodebit | object | Information about the auto debit settings for the loan.
autodebit.config | string | Shows the auto debit configuration information.
autodebit.isConfigured | boolean | Indicates whether auto debit is configured for the loan.
autodebit.isSuppressed | boolean | Indicates whether auto debit is suppressed for the loan.
notifications | object | Information about notification suppressions.
notifications.isEmailSuppressed | boolean | Indicates whether the email suppression flag has been set; if set to true, the borrower will not receive email for the loan.
notifications.isSmsSuppressed | boolean | Indicates whether the mail suppression flag has been set; if set to true, the borrower will not receive mail for the loan.
notifications.isVoiceSuppressed | boolean | Indicates whether the voice suppression flag has been set; if set to true, the borrower will not receive calls for the loan.
notifications.isWebhookSuppressed | boolean | Indicates whether webhook notifications are suppressed for the loan.
payments | object | Information about payment suppression for the loan.
payments.isAchSuppressed | boolean | Indicates whether the ACH suppression flag has been set; if set to true, ACH payments will not be drafted for the loan.
isManualSuppressed | boolean | Indicates whether manual payments are suppressed for the loan.
isCollectionCallsSuppressed | boolean | Indicates whether the collection calls suppression flag has been set; if set to true, the borrower will not receive collection calls for the loan.
isCollectionLettersSuppressed | boolean | Indicates whether the collection letters suppression flag has been set; if set to true, the borrower will not receive collection letters for the loan.
isCommunicationsSuppressed | boolean | Indicates whether communications are suppressed for the loan.
isCreditReportingSuppressed | boolean | Indicates whether the credit reporting suppression flag has been set; if set to true, credit reporting data will not be reported for the loan.
isFeesSuppressed | boolean | Indicates whether the fees suppression flag has been set; if set to true, the borrower will not accrue fees for the loan.
isPaymentDueSuppressed | boolean | Indicates whether the payment due suppression flag has been set; if set to true, the payment due date for the loan will not advance.
isStatementsSuppressed | boolean | Indicates whether the statements suppression flag has been set; if set to true, the borrower will not receive statements for the loan.
isAllSuppressed | boolean | Indicates whether all suppression options have been put in place for the loan.
loan | object | Information about the loan.
loan.loanId | string | The GUID identifier for the loan within Velocity.
loan.borrowers | object | Information about the borrower(s) 
loan.borrowers.borrowerId | string | The identifer for the borrower.
loan.borrowers.borrowerType | enum | Options: *borrower, co-borrower*.
loanProgramId | string | The identifier for the loan program associated with the loan.
lenderId | string | The identifier for the lender.
status | enum | The current loan status. Options: *charge off, default, forbearance, fraud, paid in full, rejected, repayment, write off*.
isBankruptcyActive | boolean | Indicates whether the bankruptcy flag has been set, meaning that bankruptcy is active for the loan.
isDeathActive | boolean | Indicates whether the death flag has been set, meaning that death is active for the loan.
isDisabilityActive | boolean | Indicates whether the disability flag has been set, meaning that disability is active for the loan.
isScraActive | boolean | Indicates whether the SCRA flag has been set, meaning that SCRA is active for the loan.
servicingStatus | enum | The status of the loan for servicing purposes. Options: *active, referred to collections, system of record*.