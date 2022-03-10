<!--Endpoint introduction -->
## Get Statement Details for Latest Statement

### GET /statementdetails/latest/{loanId}

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

**Returns the statement details for a loan's latest statement.**

### HTTP Request

`GET https://api.nelnet.io/loanaccounting/statementdetails/latest/{loanId}`

Parameter | Required | Type | Description
----------| -------- | ------ | -----------
loanid | yes | string (path parameter) | The GUID identifier for the loan within Velocity.

### HTTP Response

Field Name | Type | Description
---------- | ------- | -------
data | object | The response payload.
payoffAmount | number | Payoff amount as of the next due date.
lastPaymentAmount | number | Amount of last payment made.
lastPaymentDate | string | Date of last payment made.
regularPaymentAmount | number | Regularly scheduled monthly payment amount.
amountPaidCurrentCycle | number | Amount already paid this month (i.e., amount that goes towards satisfying current amount due).
daysLate | number | Numbers of days past due.
projectedLateFeeDate | string | The nextDueDate + grace days (i.e., the date a late fee will be assessed if no payment made).
projectedLateFeeAmount | number | The projected amount of late fees that will be assessed as of the above date.
remainingTerm | number | Remaining term as of the statement date.
interestRate | number | Interest rate as of the current statement date.
perDiemAmount | number | The daily interest amount as of the statement date.
pricipalBalance | number | The principal balance as of the statement date.
interestBalance | number | The outstanding unpaid interest as of the statement date.
feeBalance | number | The outstanding fees as of the statement date.
projectedInterestAccrued | number | The estimated interest that will accrue between statementDate and nextDueDate.
totalInterestAccrued | number | The total interest accrued since the first disbursement date (as of statementDate).
totalAmountPaid | number | The total amount paid since first disbursement.
sinceLastStatement | object | Statement detail information since last statement date.
sinceLastStatement.interestRate | number | Interest rate on previous statement.
sinceLastStatement.interestAccrued | number | Interest accrued between previous statement date and current statement date.
sinceLastStatement.lateFees | number | Late fees assessed since previous statement.
sinceLastStatement.nsfFees | number | Insufficient funds (NSF) fees assessed since previous statement.
sinceLastStatement.amountPaid | number | Total amount paid since previous statement.
sinceLastStatement.appliedToPrincipal | number | Amount applied to principal since previous statement.
sinceLastStatement.appliedToInterest | number | Amount applied to interest since previous statement.
sinceLastStatement.appliedToFees | number | Amount applied to fees since previous statement.
tenantId | string | The identifier for the tenant.
servicerId | string | The identifier for the servicer.
statementId | string | The identifier for the statement.
loanId | string | The identifier for the loan.
statementDate | string | The next statement date for the loan.
nextDueDate | string | The next payment due date for the loan.
currentAmountDue | number | Amount due on the next due date.
pastAmountDue | number | Past amount due.
feeAmountDue | number | Fee amount due.
totalAmountDue | number | Total amount due.
scanline | string | A unique identifier for the statement, used to associate a statement and payment.
createdDate | date | The date that the statement records were created.
updatedDate | date | The date that the statement records were last updated.