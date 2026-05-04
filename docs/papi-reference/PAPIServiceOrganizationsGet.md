# OrganizationsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceOrganizationsGet.htm_

You are here:

## OrganizationsGet

Returns list of system, library and branch level organizations. The list can be filtered by system, library, or branch.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/organizations/all
|  

|
|  
| GET
| /public/1/organizations/system
|  

|
|  
| GET
| /public/1/organizations/library
|  

|
|  
| GET
| /public/1/patron/organizations/branch
|  

### Authorization required?

Yes, if authentication level set to ALL

### XML Elements Returned

|
| Name
|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
|

Error or information message

|
|

OrganizationID

|

ID of organization

|
|

OrganizationCodeID

|

Organization code ID

1 - System
2- Library
3 -Branch

|
|

Name

|

Internal name

|
|

Abbreviation

|

Abbreviation

|
|

DisplayName

|

Name used to display to end user

|
|

ParentOrganizationID

|

The parent organization ID

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/organizations/branch

### Return - Success

|
|

HTTP/1.1 200 OK

<OrganizationsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage />

<OrganizationsGetRows>

<OrganizationsGetRow>

<OrganizationID>3</OrganizationID>

<OrganizationCodeID>3</OrganizationCodeID>

<Name>Branch A</Name>

<Abbreviation>A</Abbreviation>

<DisplayName>Library A</DisplayName>

<ParentOrganizationID>2</ParentOrganizationID>

</OrganizationsGetRow>

<OrganizationsGetRow>

<OrganizationID>4</OrganizationID>

<OrganizationCodeID>3</OrganizationCodeID>

<Name>Branch B</Name>

<Abbreviation>B</Abbreviation>

<DisplayName>Branch B</DisplayName>

<ParentOrganizationID>2</ParentOrganizationID>

</OrganizationsGetRow>

</OrganizationsGetRows>

</OrganizationsGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<OrganizationsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid type specified</ErrorMessage><OrganizationGetRows i:nil="true"/>

</OrganizationsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0