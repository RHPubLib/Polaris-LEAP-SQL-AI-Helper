# PatronMessageDelete

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronMessageDelete.htm_

You are here:

## PatronMessageDelete

Delete a specific patron message

|
|  
| DELETE
| /public/{1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/messages/{MessageType}/{MessageID}
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

MessageType

|

Yes

|

Type of message. Valid values are: *freetext* and *librarydefined*.

|
|

MessageID

|

Yes

|

ID of patron message

|
|

PatronBarcode

|

Yes

|

Barcode of patron

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

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
messages/freetext/80

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
messages/librarydefined/2

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0