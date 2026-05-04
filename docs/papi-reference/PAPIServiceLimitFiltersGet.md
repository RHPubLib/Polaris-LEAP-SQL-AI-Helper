# LimitFiltersGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceLimitFiltersGet.htm_

You are here:

## LimitFiltersGet

Returns list of valid bib search limit filters based on the organization’s Polaris System Administration values.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/limitfilters
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

**Note**: On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

Description

|

Limit filter description to display to user

|
|

CCLFilter

|

CCL filter command

|
|

DisplayOrder

|

Order in which to display this limit filter

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/74/limitfilters

### Return - Success

|
|

HTTP/1.1 200 OK

<LimitFiltersGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>3</PAPIErrorCode>

<ErrorMessage/>

<LimitFiltersRows>

<LimitFiltersRow>

<Description>All Items - This library only</Description>

<CCLFilter>AB=74</CCLFilter>

<DisplayOrder>1</DisplayOrder>

</LimitFiltersRow>

<LimitFiltersRow>

<Description>All Items - All Libraries</Description>

<CCLFilter>TOM=*</CCLFilter>

<DisplayOrder>2</DisplayOrder>

</LimitFiltersRow>

<LimitFiltersRow>

<Description>Audiobook - This library only</Description>

<CCLFilter>TOM=nsr and AB=74</CCLFilter>

<DisplayOrder>6</DisplayOrder>

</LimitFiltersRow>

</LimitFiltersRows>

</LimitFiltersGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<LimitFiltersGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid type specified</ErrorMessage>

<LimitFiltersRows i:nil="true"/>

</LimitFiltersGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0