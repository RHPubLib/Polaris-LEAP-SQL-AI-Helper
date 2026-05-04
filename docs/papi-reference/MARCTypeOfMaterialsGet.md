# MARCTypeOfMaterialsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/MARCTypeOfMaterialsGet.htm_

You are here:

## MARCTypeOfMaterialsGet

Returns a list of all MARC type of materials in the system.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/marctypeofmaterials
|  

### Authorization required?

Yes, if authentication level set to ALL.

### XML elements returned

The following table lists MARC type of materials elements returned.

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
| MARCTypeofMaterialID
| The number that coincides with the format of the work based on MARC cataloging (for example, book, audio book, DVD, or music CD)

|
| SearchCode
| Code assigned for use when searching Polaris bibliographic records by MARC type of material

|
| Description
| Description of the MARC material type

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/marctypeofmaterials

### Return - Success

|
|

HTTP/1.1 200 OK

<MARCTypeOfMaterialsGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage />

<MARCTypeOfMaterialsRows>

<MARCTypeOfMaterialsRow>

<MARCTypeOfMaterialID>1</MARCTypeOfMaterialID>

<SearchCode>bks</SearchCode>

<Description>Book</Description>

</MARCTypeOfMaterialsRow>

<MARCTypeOfMaterialsRow>

<MARCTypeOfMaterialID>2</MARCTypeOfMaterialID>

<SearchCode>mus</SearchCode>

<Description>Printed or Manuscript Music</Description>

</MARCTypeOfMaterialsRow>

</MARCTypeOfMaterialsRows>

</MARCTypeOfMaterialsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0