# MaterialTypesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/MaterialTypesGet.htm_

You are here:

## MaterialTypesGet

Returns a list of all material types in the system.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/materialtypes
|  

### Authorization required?

Yes, if authentication level set to ALL.

### XML elements returned

The following table lists material type elements returned.

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
| Error or information message.

|
| MaterialTypeID
| The material type code for item records. (for example, book, audio book, video).

|
| Description
| Description of the material type.

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/materialtypes

### Return - Success

|
|

HTTP/1.1 200 OK

<MaterialTypesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage />

<MaterialTypesRows>

<MaterialTypesRow>

<MaterialTypeID>1</MaterialTypeID>

<Description>Book</Description>

</MaterialTypesRow>

<MaterialTypesRow>

<MaterialTypeID>2</MaterialTypeID>

<Description>New / Popular Book</Description>

</MaterialTypesRow>

</MaterialTypesRows>

</MaterialTypesGetResult>

|
|  

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0