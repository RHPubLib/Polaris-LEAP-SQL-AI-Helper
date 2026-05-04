# SynchTasksPullMARCData

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/SynchTasksPullMARCData.htm_

You are here:

## SynchTasksPullMARCData

Writes information about a title available in a 3rd party system. This is used as a trigger for a call to a 3rd party vendor API to retrieve an XML MARC record for a particular unique ID. This method should only be used if a 3rd party vendor has a corresponding API with a method that allows pulling MARC record data on a record-by-record basis.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/tasks/pullMARCData
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

### Request Body XML

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

http://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/[Access token]/synch/
tasks/pullMARCData

### Body

|
|

<SynchTasksPullMARCData>

<VendorID>3M Cloud Library</VendorID>

<VendorContractID>12345</VendorContractID>

<UniqueRecordID>djhs8</UniqueRecordID>

</<SynchTasksPullMARCData>

### Return - Success

|
|

HTTP/1.1 200 OK

<SynchTasksPullMARCResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>
</SynchTasksPullMARCResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<SynchTasksPullMARCResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Failure -general</ErrorMessage>

</SynchTasksPullMARCResult>

 

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0