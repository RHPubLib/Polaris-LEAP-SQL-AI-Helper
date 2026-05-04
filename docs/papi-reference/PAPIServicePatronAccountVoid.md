# PatronAccountVoid

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronAccountVoid.htm_

You are here:

## PatronAccountVoid

This delete method voids a patron payment on the Polaris patron account. It restores the paid balance to the associated charge and the associated credit (if it was paid originally with a patron’s existing credit). The change has no impact on credit card processing; it simply voids the payment from the PatronAccount table, and a 6042 transaction is logged.

|
|  
| DELETE
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/{PatronBarcode}/account/{VoidPaymentTransactionID}/void/payment
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

|
|

VoidPaymentTransactonID

|

Yes

|

Polaris void payment transaction ID

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
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/1/ kSUEQM6CuhkF
aloIaHPYdpHJ0U7Neczl/patron/21756003332022/account/680938/void/payment

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountVoidPaymentResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronAccountVoidPaymentResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountVoidPaymentResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid workstation ID.</ErrorMessage>

</PatronAccountVoidPaymentResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0