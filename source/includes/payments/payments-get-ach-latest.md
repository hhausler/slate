<!--Endpoint introduction -->
## Get Latest ACH Payment Suppression Info for a Loan

### GET /payments/ach/suppression/latest/{loanId}

<!-- RIGHT: code samples -->

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
```

<!-- LEFT: documentation -->

**Returns latest ACH payment suppression information for a given loan.**

### HTTP Request

`GET https://api.nelnet.io/paymentapi/payments/ach/suppression/latest/{loanId}`

Parameter | Required | Type   | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The identifier for the loan to return records for.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload. All of the following is contained within `data`.
paymentSuppressionId | string | The identifier for the ACH payment suppression.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
loanId | string | The identifier for the loan.
lenderId | string | The identifier for the lender.
effectiveDate | string | The effective date for the ACH payment suppression setting.
suppressionType | enum | The suppression type.
suppressionReason | enum | The suppression reason.
isSuppressed | boolean | Indicates whether ACH payments are suppressed for the loan.
createdDate | date | The date that the suppression setting was created.
createdBy | object | Information about the user who created the suppression setting.