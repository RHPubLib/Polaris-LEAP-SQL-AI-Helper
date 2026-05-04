# PatronAccountCreateCredit

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronAccountCreateCredit.htm_

You are here:

## PatronAccountCreateCredit

This method creates a credit on the Polaris patron account.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/{PatronBarcode}/account/createcredit
|  

### Authorization required?

Yes

### Protected method?

Yes

### URI Parameters

|
|

Name

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

Patron barcode

### Query String Parameters

|
|

Name

|

Values

|

Required

|

Description/Notes

|
|

wsid

|

>0

|

Yes

|

ID of workstation calling this method

|
|

userid

|

>0

|

Yes

|

ID of user calling this method (not patron ID)

### XML Body Elements

**Important:**XML elements must be in the order shown below.

|
|

Name

|

Required

|

Description/Notes

|
|

TxnAmount

|

Yes

|

Valid dollar amount and not greater than balance owed

|
|

PaymentMethodID

|

Yes

|

Valid values are:

11 - Cash
12 - Credit card
13 - Debit card
14 - Check
15 - Voucher
17 - Smart card

|
|

FreeTextNote

|

Yes

|

Note to attach to payment

### XML Elements Returned

The following XML elements are returned.

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

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/account/createcredit

### Body

|
|

<PatronAccountCreateCreditData>

<TxnAmount >1.25</TxnAmount>

<PaymentMethodID >11</PaymentMethodID>

<FreeTextNote>Credited through Polaris API</FreeTextNote>

</PatronAccountCreateCreditData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountCreateCreditResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronAccountCreateCreditResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountCreateCreditResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid workstation ID.</ErrorMessage>

</PatronAccountCreateCreditResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0