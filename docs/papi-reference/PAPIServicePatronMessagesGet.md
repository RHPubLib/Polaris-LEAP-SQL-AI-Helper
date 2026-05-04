# PatronMessagesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronMessagesGet.htm_

You are here:

## PatronMessagesGet

Retrieves a list of new and read patron messages.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/messages
|  

### Authorization required?

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

Required

|

Description/Notes

|
|

unreadonly

|

 

|

Set to 1 to return only new messages.

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
|

Type

|

0 = Freetext message
1 = Library defined

|
|

ID

|

Message ID

|
|

OrgName

|

Name of organization that created the message

|
|

Date

|

Date message was created

|
|

Value

|

Message text

|
|

isRead

|

Has the message been marked as read

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/messages

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/217560033
32022/messages?unreadonly=1

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0