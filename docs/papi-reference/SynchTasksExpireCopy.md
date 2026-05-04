# SynchTasksExpireCopy

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/SynchTasksExpireCopy.htm_

You are here:

## SynchTasksExpireCopy

This method is used to inform the Polaris ILS when a copy of a title in the library's eContent collection has expired and is no longer available for check out. For certain publishers this expiration may be time-based; for others the expiration may be based on a particular number of check-out transactions.

|
|  
| POST
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/tasks/expirecopy
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

### XML Elements Returned

|
|

Name

|

Description/Notes

|
|

PAPIErrorCode

|

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
|

ErrorMessage

| Error or information message

### Example

|
|

http://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/[Accesstoken]/synch/tasks/
expirecopy

### Body

|
|

<SynchTasksExpireCopyData>

<VendorID>3M Cloud Library</VendorID>

<VendorContractID>cezmf</VendorContractID>

<UniqueRecordID>tomg9</UniqueRecordID>

<PatronBarcode/>

<TransactionDateTime>2012-09-02T00:00:00</TransactionDateTime>

</SynchTasksExpireCopyData>

### Return - Success

|
|

HTTP/1.1 200 OK

<SynchTasksExpireCopyResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</SynchTasksExpireCopyResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<SynchTasksExpireCopyResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Failure -general</ErrorMessage>

</SynchTasksExpireCopyResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0