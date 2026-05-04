# PatronTitleListDeleteTitle

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListDeleteTitle.htm_

You are here:

## PatronTitleListDeleteTitle

Deletes a single specified bibliographic record from the specified list in the patron account.

|
|  
| DELETE
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistdeletetitle?list={list_id}&position={position_id}
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

|
| list_id
| Yes
| Unique identifier for the list

|
| position_id
| Yes
| ID of the position in the list

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
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patrontitlelistdeletetitle?list=700&position=4

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListDeleteTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage/>

</PatronTitleListDeleteTitleResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListDeleteTitleResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Could not remove record because the record store does not exist.</ErrorMessage>

</PatronTitleListDeleteTitleResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0