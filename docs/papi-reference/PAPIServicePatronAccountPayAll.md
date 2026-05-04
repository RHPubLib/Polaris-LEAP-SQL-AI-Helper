# PatronAccountPayAll

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronAccountPayAll.htm_

You are here:

## PatronAccountPayAll

This method takes a payment amount, a note, and a payment method, and applies the payments to all patron charges, paying off the oldest charges first. It allows a partial pay all, but not an overpayment. If the amount is greater than the amount the patron currently owes in charges, a -3610 error is returned.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/{PatronBarcode}/account/
lumpsumpayment
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

Barcode of patron

### Query String Parameters

|
| Name
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

**Important:** XML elements must be in the order shown below.

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

### XML elements returned

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
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/1/kSUEQM6CuhkFaloIaHPYdp
HJ0U7Neczl/patron/21756003332022/account/lumpsumpayment

### Body

|
|

<PatronAccountPayData>

<TxnAmount >1.25</TxnAmount>

<PaymentMethodID >11</PaymentMethodID>

<FreeTextNote>Paid through Polaris API</FreeTextNote>

</PatronAccountPayData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountPayResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronAccountPayResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountPayResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid workstation ID.</ErrorMessage>

</PatronAccountPayResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0