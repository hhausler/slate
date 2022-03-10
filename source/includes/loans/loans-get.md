<!--Endpoint introduction -->
## Get Loans

### GET /loans

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl -X GET \
  https://api.nelnet.io/loanapi/loans?loannumber=212049743522 \
  -H 'Accept: */*' \
  -H 'Accept-Encoding: gzip, deflate' \
  -H 'Authorization: <ACCESS TOKEN>' \
  -H 'Cache-Control: no-cache' \
  -H 'Connection: keep-alive' \
  -H 'Host: api.nelnet.io' \
  -H 'cache-control: no-cache'

```

```csharp
var client = new RestClient("https://api.nelnet.io/loanapi/loans");
var request = new RestRequest(Method.GET);
request.AddHeader("cache-control", "no-cache");
request.AddHeader("Connection", "keep-alive");
request.AddHeader("Accept-Encoding", "gzip, deflate");
request.AddHeader("Host", "api.nelnet.io");
request.AddHeader("Cache-Control", "no-cache");
request.AddHeader("Accept", "*/*");
request.AddHeader("Authorization", "<ACCESS TOKEN>");
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

xhr.open("GET", "https://api.nelnet.io/loanapi/loans");
xhr.setRequestHeader("Authorization", "<ACCESS TOKEN>");
xhr.setRequestHeader("Host", "api.nelnet.io");
xhr.setRequestHeader("cache-control", "no-cache");

xhr.send(data);

```

```python
import http.client

conn = http.client.HTTPConnection("api,nelnet,io")

headers = {
    'Authorization': "<ACCESS TOKEN>",
    'Accept': "*/*",
    'Cache-Control': "no-cache",
    'Host': "api.nelnet.io",
    'Accept-Encoding': "gzip, deflate",
    'Connection': "keep-alive",
    'cache-control': "no-cache"
    }

conn.request("GET", "loanapi,loans", headers=headers)

res = conn.getresponse()
data = res.read()

```

> JSON returned:

```json
{
    "data": [
        {
            "loanId": "2c809e08-a5ba-4559-9c1c-4ac2555fb1e6",
            "loanNumber": "212049743522",
            "loanNumberFormatted": "2120-4974-3522",
            "borrowers": [
                {
                    "borrowerId": "9f732dec-93fa-4f5f-948c-30da4271c48f",
                    "borrowerType": "borrower"
                }
            ],
            "investors": null,
            "loanProgramId": "3cc0d3c0-8465-47bd-81a2-ccd22aa09487",
            "lenderId": "e6310976-06ab-4ddd-8d48-58683e94c246",
            "term": 30,
            "amount": 2000,
            "interestRate": 30,
            "rateType": "Fixed",
            "minInterestRate": 0,
            "maxInterestRate": 30,
            "margin": 0,
            "dueDay": 18,
            "disbursementDate": "2019-07-04",
            "firstPaymentDate": "2019-07-18",
            "status": "repayment",
            "termFrequency": "bi-weekly",
            "externalReferenceId": "538848707",
            "onboardingId": null,
            "customData": null,
            "isActive": true,
            "isScraActive": false,
            "isBankruptcyActive": false,
            "isDeathActive": false,
            "isDisabilityActive": false,
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
            "updatedDate": "2019-10-16T18:32:56.934Z",
            "originationFee": null
        }
    ],
    "paging": {
        "offset": 0,
        "limit": 20,
        "links": {
            "first": "/loans?offset=0&limit=20",
            "last": "/loans?offset=0&limit=20"
        }
    }
}

```

<!-- LEFT: documentation -->

**Gets all loans and basic loan information.**

Pass a query parameter, such as `externalreferenceid`, to narrow results.

### HTTP Request

`GET https://api.nelnet.io/loanapi/loans`

The request can have any of the following query parameters.

Parameter | Type | Description
----------| ------- | -------
lenderid | string | A lender identifier. Use to return loan(s) associated with a given lender.
investorid | string | An investor identifier. Use to return loan(s) associated with a given investor.
loanprogramid | string | A loan program identifier. Use to return loan(s) associated with a given loan program.
borrowerid | string | A borrower GUID identifier. Use to return loan(s) for a given borrower.
externalreferenceid | string | An external identifier or reference number. Use to return a specific loan.
loannumber | string | A loan GUID identifier. Use to return a specific loan.
offset | number | The paging offset. Default value: 0.
limit | number | The paging limit. Default value: 20.

### HTTP Response

The response object `PagedResponseBodyLoan` contains two large objects, `paging` and `data`.

**Paging Object**

Field Name | Type | Description
---------- | ------- | -------
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
loanId | string | The GUID loan identifier.
loanNumber | string | The "friendly ID" for the loan within Velocity.
loanNumberFormatted | string | The formatted loan number.
tenantId | string | The tenant identifier.
servicerId | string | The servicer identifier.
borrowers | object | Information about the borrower(s) associated with the loan(s) returned.
borrowers.borrowerId | string | The identifier (within Velocity) for the borrower.
borrowers.borrowerType | enum | Options: *borrower, co-borrower*.
investors | object | Information about lenders.
investorId | string | The identifier(s) for investor(s) associated with the loan(s) returned.
loanProgramId | string | The identifier for the loan program.
lenderId | string | The identifier for the lender(s) associated with the loan(s) returned.
term | integer($int32) | The loan term.
amount | number($double) | The total loan amount.
interestRate | number($double) | The loan interest rate.
minInterestRate | number($double) | The minimum interest rate for the loan(s) returned.
maxInterestRate | number($double) | The maximum interest rate for the loan(s) returned.
margin | number($double) | The loan margin amount. For fixed-term loans, this will be set to 0.
rateType | string | The loan rate type, either *fixed* or *variable*.
dueDay | number($double) | The payment due day for the loan(s).
disbursementDate | string | The date on which the loan funds were disbursed to the borrower, in the *YYYY-MM-DD* format.
firstPaymentDate | string | The borrower's first payment due date, in the *YYYY-MM-DD* format.
status | enum | The current loan status. Options: *charge off, default, forbearance, fraud, paid in full, rejected, repayment, write off*.
termFrequency | enum | The term frequency of the loan. Options: *monthly, bi-weekly, weekly, quarterly*.
externalReferenceId | string | The external identifier or reference number for the borrower.
onboardingId | string | The identifier for the onboarding bundle assigned when the borrower was added (via call to the Onboarding service) to Velocity.
customData | object | Contains any custom data fields added to the loan record.
createdDate | string($date-time) | Date on which the loan record was created.
updatedDate | string($date-time) | Date on which the borrower record was last updated, if applicable.
updatedBy | object | The identifier for the token associated with the latest update, if any.
createdBy | object | The identifier for the token associated with the loan creation.
isActive | boolean | Shows whether the loan is in active status.
isScraActive | boolean | Shows whether the loan has an active servicemember flag.
isBankruptcyActive | boolean | Shows whether the loan has an active bankruptcy flag.
isDeathActive | boolean | Shows whether the loan has an active death flag.
isDisabilityActive | boolean | Shows whether the loan has an active disability flag.
originationFee | number($double) | The fee, if any, charged at the time of origination.
paymentAmount | number($double) | The amount of the payment regularly due for the loan.