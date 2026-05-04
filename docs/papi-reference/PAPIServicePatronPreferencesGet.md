# PatronPreferencesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronPreferencesGet.htm_

You are here:

## PatronPreferencesGet

Return preferences for a patron including reading list, email format, and notification type.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/preferences
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

Barcode of patron

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

|
| PatronID
| ID of patron

|
| Barcode
| Patron barcode

|
| ReadingListEnabled
| Should Polaris maintain a reading list of items previously checked out to the patron.

|
|

DeliveryMethodID

|

ID of how notifications should be delivered

1 - Mailing Address
2 - Email Address
3 - Telephone 1
4 - Telephone 2
5 - Telephone 3
6 - FAX
7 - EDI

|
|

DeliveryMethodDescription

|

Description of how notifications should be delivered. When a patron does not have a delivery method, PAPI returns a description of “null” rather than “none”.

|
|

DeliveryEmailFormatID

|

ID of the type of format of Polaris-generated email messages

1 - Plain text
2 - HTML

|
|

DeliveryEmailFormatDescription

|

Description of the type of format of Polaris-generated email messages

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
preferences

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronPreferencesGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronPreferences>

<PatronID>299377</PatronID>

<Barcode>21756003332022</Barcode>

<ReadingListEnabled>true</ReadingListEnabled>

<DeliveryMethodID>3</DeliveryMethodID>

<DeliveryMethodDescription>Telephone 1</DeliveryMethodDescription>

<DeliveryEmailFormatID>2</DeliveryEmailFormatID>

<DeliveryEmailFormatDescription>HTML</DeliveryEmailFormatDescription>

</PatronPreferences>

</PatronPreferencesGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronPreferencesGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Example error message</ErrorMessage>

<PatronPreferences/>

</PatronPreferencesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0