# PatronAccountRefundCredit

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronAccountRefundCredit.htm_

You are here:

## PatronAccountRefundCredit

This method refunds credits on the Polaris patron account, with the oldest credits processed first.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/{PatronBarcode}/account/
lumpsumrefundcredit
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

ID of workstation calling this method.

|
|

userid

|

>0

|

Yes

|

ID of user calling this method (not patron ID).

### XML Body Elements

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

| Yes
| Valid dollar amount

|
| FreeTextNote
| No
|

Note to attach to payment

### XML Elements Returned

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
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/account/
lumpsumrefundcredit

### Body

|
|

<PatronAccountRefundCreditData>

<TxnAmount >1.25</TxnAmount>

<FreeTextNote>Credited through Polaris API</FreeTextNote>

</PatronAccountRefundCreditData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountRefundCreditResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/></PatronAccountRefundCreditResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountRefundCreditResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid workstation ID.</ErrorMessage>

</PatronAccountRefundCreditResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0