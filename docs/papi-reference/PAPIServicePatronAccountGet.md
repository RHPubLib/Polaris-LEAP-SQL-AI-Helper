# PatronAccountGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronAccountGet.htm_

You are here:

## PatronAccountGet

Returns list of fines and fees associated with a specified patron. The list can be filtered by outstanding (current) or reconciled (historical) fines and fees.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/account/outstanding
|  

|
|  
| GET
| /public/1/patron/{PatronBarcode}/account/reconciled
|  

### Authorization required?

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

Barcode of patron.

### XML Elements Returned

One or more fines and fees associated with the patron. The list is sorted in ascending order by transaction date.

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

TransactionID

|

Polaris ID of the transaction

|
|

TransactionDate

|

Date and time the transaction was logged

|
|

BranchID

|

Polaris ID of the branch associated with the fine

|
|

BranchName

|

Name of the branch associated with the fine

|
|

TransactionTypeID

|

Polaris ID of the type of transaction

1 - Charge
2 - Payment for a Charge
3 - Return from Deposit
4 - Deposit
5 - Waive
6 - Waive Existing Charge
7 - Forfeit from Deposit
8 - Credit from Deposit/Pay
9 - Refund from Payment
10 - Auto-waive

|
|

TransactionTypeDescription

|

Description of the type of transaction

|
|

FeeDescription

|

Detailed description of the fee

|
|

TransactionAmount

|

Amount of transaction in dollar and cents

|
|

OutstandingAmount

|

Outstanding amount

|
|

FreeTextNote

|

Free text note associated with the transaction

|
|

ItemID

|

Polaris ID of the associated item record

|
|

Barcode

|

The item barcode

|
|

BibID

|

The ID of the associated bibliographic record

|
|

FormatID

|

Polaris ID of the type of format (see Material Format Types)

|
|

FormatDescription

|

Format description

|
|

Title

|

Title of the item

|
|

Author

|

Author of the item

|
|

CallNumber

|

Call Number of the item

|
|

CheckOutDate

|

Date the item associated with the fine was checked out

|
|

DueDate

|

The original due date of the item associated with the fine

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022
/account/outstanding

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronAccountGetRows>

<PatronAccountGetRow>

<TransactionID>3605602</TransactionID>

<TransactionDate>2009-09-09T17:18:31</TransactionDate>

<BranchID>3</BranchID>

<BranchName>Amsterdam Free Library</BranchName>

<TransactionTypeID>1</TransactionTypeID>

<TransactionTypeDescription>Charge</TransactionTypeDescription>

<FeeDescription/>

<TransactionAmount>2.0000</TransactionAmount>

<OutstandingAmount>2.0000</OutstandingAmount>

<FreeTextNote/>

<ItemID>0</ItemID>

<Barcode/>

<BibID>0</BibID>

<FormatID>0</FormatID>

<FormatDescription/>

<Title/>

<Author/>

<CallNumber/>

<CheckOutDate>0001-01-01T00:00:00</CheckOutDate>

<DueDate>0001-01-01T00:00:00</DueDate>

</PatronAccountGetRow>

...

</PatronAccountGetRows>

</PatronAccountGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid type specified</ErrorMessage>

<PatronAccountGetRows i:nil="true"/>

</PatronAccountGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0