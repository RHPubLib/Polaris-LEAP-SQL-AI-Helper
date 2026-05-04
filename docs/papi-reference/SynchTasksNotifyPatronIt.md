# SynchTasksNotifyPatronItem

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/SynchTasksNotifyPatronIt.htm_

You are here:

## SynchTasksNotifyPatronItem

Writes patron notification transaction information into the Polaris database for additional processing within the Polaris ILS. This method is to be used for when a message relates to a specific patron/title combination.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/tasks/notifypatronitem
|  

### Authorization required?

Yes

### Query String Parameters

|
|

Name

|

Value

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

No

|

ID of workstation calling this method

|
|

userid

|

>0

|

No

|

ID of user calling this method (not patron ID)

### XML Body Elements

**Important: **XML elements must be in the order shown below.

|
|

Name

|

Description/Notes

|
| VendorID
| Free text string. Consult with Polaris.

|
| VendorContractID
| Free text string. Consult with Polaris.

|
| UniqueRecordID
| The record ID in thrid-party system that identifies the title.

|
| PatronBarcode
| The Patron barcode, as represented in Polaris.

|
| Message
|  

### Example

|
|

http://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/[Access token]/synch/
tasks/notifypatronitem

### Body

|
|

<SynchTasksNotifyPatronItemData>

<VendorID>3M Cloud Library</VendorID>

<VendorContractID>12345</VendorContractID>

<UniqueRecordID>djhs8</UniqueRecordID>

<PatronBarcode>1000200692332</PatronBarcode>

<Message>This title is on hold for you.</Message>

</SynchTasksNotifyPatronItemData>

### Return - Success

|
|

HTTP/1.1 200 OK

<SynchTasksNotifyPatronItemResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</SynchTasksNotifyPatronItemResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<SynchTasksNotifyPatronItemResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-3000</PAPIErrorCode>

<ErrorMessage>Error retrieving patron ID.</ErrorMessage>

</SynchTasksNotifyPatronItemResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0