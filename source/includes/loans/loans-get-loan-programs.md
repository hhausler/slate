<!--Endpoint introduction -->
## Get Loan Programs

### GET /loanprograms

<!-- RIGHT: code samples -->

> Sample request:

```shell
curl --location --request GET 'https://api.nelnet.io/loanprogramapi/loanprograms?limit=2' \
--header 'tenantid: 314' \
--header 'servicerid: 2' \
--header 'Authorization: <ACCESS TOKEN>' \
--data-raw ''
```

```csharp
var client = new RestClient("https://api.nelnet.io/loanprogramapi/loanprograms?limit=2");
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

xhr.open("GET", "https://api.nelnet.io/loanprogramapi/loanprograms?limit=2");
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
conn.request("GET", "/loanprogramapi/loanprograms?limit=2", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

> JSON returned:

```json
{
    "data": [
        {
            "loanProgramId": "0038ac8d-1f1a-4c25-b056-96b7e841cb45",
            "description": "Dev Loan Program",
            "paymentSettings": {
                "order": "fees/interest/principal",
                "feeOrder": "lender/servicer/investor",
                "agingDays": 1,
                "tolerance": {
                    "amount": 2,
                    "amountType": "dollar"
                },
                "alwaysPullAutoDebit": true,
                "minimumPaymentAmount": 10
            },
            "interestSettings": {
                "method": "actual/actual",
                "frequency": "monthly"
            },
            "billingSettings": {
                "days": "25",
                "termFrequency": "monthly",
                "isDueDateChangeAllowed": false
            },
            "feeSettings": {
                "nsfFeeSettings": {
                    "feeAmount": 60,
                    "graceDays": 0,
                    "maximumFee": 60,
                    "minimumFee": 10,
                    "feeAmountType": "dollar",
                    "feeProceedsType": "lender"
                },
                "lateFeeSettings": {
                    "feeAmount": 60,
                    "graceDays": 10,
                    "maximumFee": 100,
                    "minimumFee": 10,
                    "feeAmountType": "dollar",
                    "feeProceedsType": "lender"
                }
            },
            "isActive": true,
            "isBatchActive": false,
            "createdDate": "2020-01-15T19:31:16.556Z",
            "updatedDate": "2020-07-13T22:26:40.311Z",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "incentiveSettings": {
                "autoDebitSettings": {
                    "amount": 0.25
                }
            },
            "delinquencySettings": {
                "calls": {
                    "dialerBuckets": [
                        {
                            "attempts": 10,
                            "contacts": 1,
                            "daysLateEnd": 30,
                            "daysLateStart": 1
                        },
                        {
                            "attempts": 10,
                            "contacts": 1,
                            "daysLateEnd": 60,
                            "daysLateStart": 31
                        },
                        {
                            "attempts": 10,
                            "contacts": 1,
                            "daysLateEnd": 90,
                            "daysLateStart": 61
                        },
                        {
                            "attempts": 10,
                            "contacts": 1,
                            "daysLateEnd": 120,
                            "daysLateStart": 91
                        }
                    ]
                },
                "letters": {
                    "daysLate": [
                        15,
                        25,
                        35,
                        45,
                        55,
                        65,
                        90
                    ]
                },
                "defaultDays": 121
            },
            "customData": {
                "test": "value"
            }
        },
        {
            "loanProgramId": "003f35d1-8da1-440d-95e5-21dc7180fb31",
            "description": "U-fi Personal Loan",
            "paymentSettings": {
                "order": "fees/interest/principal",
                "feeOrder": "lender/servicer/investor",
                "agingDays": 15,
                "minimumPaymentAmount": 0
            },
            "interestSettings": {
                "method": "actual/actual",
                "frequency": "monthly"
            },
            "billingSettings": {
                "days": 21,
                "frequency": "monthly",
                "termFrequency": "monthly",
                "isDueDateChangeAllowed": true
            },
            "feeSettings": {
                "nsfFeeSettings": {
                    "feeAmount": 60,
                    "graceDays": 0,
                    "maximumFee": 60,
                    "minimumFee": 10,
                    "feeAmountType": "dollar",
                    "feeProceedsType": "servicer"
                },
                "lateFeeSettings": {
                    "feeAmount": 60,
                    "graceDays": 10,
                    "maximumFee": 100,
                    "minimumFee": 10,
                    "feeAmountType": "dollar",
                    "feeProceedsType": "lender"
                }
            },
            "isActive": true,
            "isBatchActive": false,
            "createdDate": "2019-05-09T20:30:06.795Z",
            "updatedDate": "2019-05-09T20:30:06.795Z",
            "lenderId": "bbfc1a01-61d4-4556-afac-3f98b970e397",
            "incentiveSettings": {
                "autoDebitSettings": {
                    "amount": 0.25
                }
            },
            "delinquencySettings": null,
            "customData": null
        }
    ],
    "paging": {
        "rows": 1198,
        "pages": 599,
        "offset": 0,
        "limit": 2,
        "links": {
            "first": "/loanprograms?offset=0&limit=2",
            "last": "/loanprograms?offset=1198&limit=2",
            "next": "/loanprograms?offset=2&limit=2"
        }
    }
}
```

<!-- LEFT: documentation -->

**Returns loan programs.**

### HTTP Request

`GET https://api.nelnet.io/loanprogramapi/loanprograms`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
lenderid | no | string | The identifier for the lender. Use to return only loan program records for a given lender.
offset | no | number | Use to set which record to start with in the response. Defaults to 0.
limit | no | number | Use to limit the number of records returned in the response. Defaults to 20.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
paging | object | Information about the paging of the results returned, within the total results available.
paging.offset | number ($double) | The starting record in the return - the offset between the records returned and list of total records.
paging.limit | number ($double) | The number of records per page.
paging.links | object | Information about the pagination and links in the response.
paging.links.first | string | A link to the first page of records returned.
paging.links.last | string | A link to the last page of records returned.
paging.links.previous | string | A link to the previous page in the list of records returned.
paging.links.next | string | A link to the next page in the list of records returned.
data | object | The response payload. All of the following fields exist within `data`.
loanProgramId | string | The identifier for the loan program.
description | string | A general description for the loan program record.
isActive | boolean | Indicates whether the loan program is active in the system.
isBatchActive | boolean | Indicates whether the loan program batch is active.
lenderId | string | The identifier for the lender.
billingSettings | object | Information about billing settings.
billingSettings.days | number | Number of days in the billing cycle.
billingSettings.termFrequency | enum | The term frequency of the loan. Options: *monthly, bi-weekly, weekly, quarterly.*
billingSettings.isDueDateChangeAllowed | boolean | Indicates whether due date changes are allowed in the loan program.
delinquencySettings | object | Information about delinquency settings.
delinquencySettings.letters | object | Information about the delinquency settings.
delinquencySettings. letters.daysLate | string | Sets the number of days late that a delinquency letter is set.
calls | object | Information about call settings for the loan program.
calls.dialerBuckets | object | Information about dialer buckets. Buckets are a range of days past due as defined by the loan program settings. Attempts are the number of call attempts allowed within that timeframe. *Example: For loans that are 1-15 days past due (bucket), make 4 call attempts (attempts) and stop after 1 contact is made (contacts).*
calls.dialerBuckets. daysLateStart | number | The number of days past due that sets the start of the delinquency bucket.
calls.dialerBuckets. daysLateEnd | number | The end of the delinquency bucket.
calls.dialerBuckets. attempts | number | Number of attempts.
calls.dialerBuckets. contacts | number | Number of contacts.
calls.defaultDays | number | The loan can't be defaulted before this many days past due.
feeSettings | object | Information about fee settings.
feeSettings.lateFeeSettings | object | Information about late fee settings.
feeSettings.lateFeeSettings. graceDays | number | The number of days after the payment due date before a late fee is assessed.
feeSettings.lateFeeSettings. feeAmount | number | The amount of the late fee.
feeSettings.lateFeeSettings. feeAmountType | enum | The late fee type. Options: *flat rate*, *percentage*, *percent of past-due amount*.
feeSettings.lateFeeSettings. feeProceedsType | enum | Where the fee proceeds should go. Options: to the *lender*, *investor*, *servicer*.
feeSettings.lateFeeSettings. minimumFee | number | The minimum late fee (in dollars).
feeSettings.lateFeeSettings. maximumFee | number | The maximum late fee (in dollars).
feeSettings.nsfFeeSettings | object | Information about insufficient funds (NSF) settings.
feeSettings.nsfFeeSettings. feeAmount | number | The fee amount for insufficient funds.
feeSettings.nsfFeeSettings. feeAmountType | enum | The NSF fee amount type. Options: *dollar*, *percentage*.
feeSettings.nsfFeeSettings. feeProceedsType | enum | Where the fee proceeds should go. Options: to the *lender*, *investor*, *servicer*.
feeSettings.nsfFeeSettings. minimumFee | number | The minimum fee amount.
feeSettings.nsfFeeSettings. maximumFee | number | The maximum fee amount.
feeSettings.incentiveSettings | object | Information about incentive settings.
feeSettings.incentiveSettings. autoDebitSettings | object | Information about auto debit settings.
feeSettings.incentiveSettings. autoDebitSettings. amount | number | The amount that the interest rate will be reduced by.
feeSettings.interestSettings | object | Information about the interest settings.
feeSettings.interestSettings. method | enum | The interest rate method. Options: *actual/actual*, *30/360*, *actual/365*, *actual/365.25*.
feeSettings.interestSettings. frequency | enum | The frequency of the interest rate accrual.
paymentSettings | object | Information about payment settings.
paymentSettings.order | enum | The order that payments are applied. Options: *fees/interest/principal*, *interest/fees/principal*.
paymentSettings. feeOrder | enum | The order that fees are applied. Options: *lender/servicer/investor*, *lender/investor/servicer*, *servicer/lender/investor*, *servicer/investor/lender*, *investor/servicer/lender*, *investor/lender/servicer*.
paymentSettings. minimumPaymentAmount | number | The minimum payment amount per billing cycle for any loan.
paymentSettings. agingDays | number | The number of days after a payment is effective that a refund can be sent out.
paymentSettings. alwaysPullAutoDebit | boolean | Indicates whether the system should always pull auto debit, even if the amount due is $0.
paymentSettings.tolerance | object | Information about payment setting tolerance.
paymentSettings.tolerance. amount | number | The payment tolerance amount.
paymentSettings.tolerance. amountType | enum | The tolerance type, either dollar amount or percentage.
communicationSettings | object | Information about communications settings.
communicationSettings. communicationSettingId | string | The identifier for the communication setting.
communicationSettings. loanProgramId | string | The identifier for the loan program.
communicationSettings. tenantId | string | The identifier for the tenant.
communicationSettings. servicerId | string | The identifier for the servicer.
communicationSettings. code | string | The communication code.
communicationSettings. name | string | The name of the communication.
communicationSettings. type | enum | The communication type.
communicationSettings. event | string | The trigger for the communication.
communicationSettings. provider | string | The name of the communication provider/integration name.
communicationSettings. dataBlocks | object | Information about the communication.
communicationSettings. dataBlocks.dataBlock | object | The data blocks included in the communication. Options: *autoDebitDetails, borrowerDetails, callTrackingSummary, currentDelinquencyDialerBucket, paymentDetails, loanDetails, scheduledPaymentDetails, scraDenialDetails, statementDetails*.
communicationSettings. parameters | object | Communication parameters.
communicationSettings. suppressionTags | string | Tags on the communication for suppression purposes (used for suppressing all communications tagged *delinquency*).
communicationSettings. isActive | boolean | Indicates whether the communication settings are active.
communicationSettings. createdDate | date | The date that the setting was created.
communicationSettings. updatedDate | date | The date that the setting was last updated.
communicationSettings. createdBy | object | Information about the user who created the communication setting.
communicationSettings. updatedBy | object | Information about the user who last updated the communication setting.
customData | object | Borrower custom data.
createdDate | date | When the loan program record was created.
updatedDate | date | The last time the loan program was updated (if applicable).
