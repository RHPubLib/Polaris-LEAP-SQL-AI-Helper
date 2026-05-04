# PatronMessageUpdateStatus

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronMessageUpdateStatus.htm_

You are here:

## PatronMessageUpdateStatus

Marks a message as read.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/messages/{MessageType}/{MessageID}
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
|

MessageType

|

Yes

|

Type of message. Valid values:

freetext
librarydefined

|
|

MessageID

|

Yes

|

ID of patron message

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

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/217560033
32022/messages/freetext/80

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/217560033
32022/messages/librarydefined/2

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0