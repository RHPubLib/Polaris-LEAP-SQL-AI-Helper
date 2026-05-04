# SynchTasksCheckin

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/SynchTasksCheckin.htm_

You are here:

## SynchTasksCheckin

Writes checkin transaction information into the Polaris database for additional processing within the Polaris ILS.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/tasks/checkin
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
| TransactionDateTime
| Use GMT, ex. 2012-06-01T11:00:00.

|
| PatronVendorContractID
| The ID of the patron vendor contract.

### HML Elements Returned

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

### Example

|
|

http://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/[Access token]/synch/
tasks/checkin

### Body

|
|

<SynchTasksCheckinData>

<VendorID>3M Cloud Library</VendorID>

<VendorContractID>12345</VendorContractID>

<UniqueRecordID>djhs8</UniqueRecordID>

<PatronBarcode>1000200692332</PatronBarcode>

<TransactionDateTime>2012-06-01T11:00:00</TransactionDateTime>

</SynchTasksCheckinData>

### Return - Success

|
|

HTTP/1.1 200 OK

<SynchTasksCheckinResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</SynchTasksCheckinResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<SynchTasksCheckinResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance"><

PAPIErrorCode>-3000</PAPIErrorCode>

<ErrorMessage>Error retrieving patron ID.</ErrorMessage>

</SynchTasksCheckinResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0