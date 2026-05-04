# PatronStatisticalClassesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronStatisticalClassesGet.htm_

You are here:

## PatronStatisticalClassesGet

Returns a list of patron statistical classes based on the organization ID.

-

To retrieve a list of all patron statistical classes in the system, pass in an organization ID of 1.

-

To retrieve a list of patron statistical classes for a specific branch, pass in the branch ID.

|
|  
| GET
|

/public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patronstatisticalclasses

|  

### Authorization required?

No

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

Version

|

Yes

|

Version of PAPI used

|
| LangID
| Yes
| Patron's language identifier

|
| AppID
| Yes
| ID of the calling application

|
| OrgID
| Yes
| A system-level or branch-level organization identifier

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
| StatisticalClassID
| Patron statistical class code ID

|
| OrganizationID
| Organization where statistical class code is defined

|
| Description
| Statistical class code description

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patronstatisticalclasses

### Success

|
|

<PatronStatisticalClassesGetResult>

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<PatronStatisticalClassesRows>

<PatronStatisticalClassesRow>

<StatisticalClassID>0</StatisticalClassID>

<OrganizationID>0</OrganizationID>

<Description>string</Description>

</PatronStatisticalClassesRow>

</PatronStatisticalClassesRows>

</PatronStatisticalClassesGetResult>

### Return - Failed

|
|

<PatronStatisticalClassesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-103</PAPIErrorCode>

<ErrorMessage>Too many matching rows; try again with a different organization</ErrorMessage>

<PatronStatisticalClassesRows />

</PatronStatisticalClassesGetResult>

### Error Messages

|
Code
Description

|
| -103
| Row limit exceeded

|
| -5000
| Invalid OrganizationID supplied

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0