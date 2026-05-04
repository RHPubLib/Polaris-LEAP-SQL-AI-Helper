# SysHoldStatusesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/SysHoldStatusesGet.htm_

You are here:

## SysHoldStatusesGet

Returns a list of all hold statuses in the system.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/sysholdstatuses
|  

### Authorization required?

Yes, if authentication level set to ALL.

### XML elements returned

The following table lists system hold status elements returned.

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
| SysHoldStatusID
| The number that coincides with the system hold status.

|
| Description
| Description of the system hold status

|
| Name
| Name of the system hold status

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/sysholdstatuses

### Result - Success

|
|

HTTP/1.1 200 OK

<SysHoldStatusesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage />

<SysHoldStatusesRows>

<SysHoldStatusesRow>

<SysHoldStatusID>1</SysHoldStatusID>

<Description>Inactive</Description>

<Name>Inactive</Name>

</SysHoldStatusesRow>

<SysHoldStatusesRow>

<SysHoldStatusID>2</SysHoldStatusID>

<Description>Active</Description>

<Name>Active</Name>

</SysHoldStatusesRow>

</SysHoldStatusesRows>

</SysHoldStatusesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0