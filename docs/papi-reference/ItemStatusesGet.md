# ItemStatusesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ItemStatusesGet.htm_

You are here:

## ItemStatusesGet

Returns a list of all item statuses in the system.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/itemstatuses
|  

### Authorization Required

Yes, if authentication level set to ALL.

### XML elements returned

The following table lists item status elements returned.

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
| ItemStatusID
| The unique circulation code for items (for example, in, out, in-transit, and withdrawn)

|
| Description
| Text description of the item status. Can be modified in the staff client.

|
| Name
| Name of item status used in circulation processing

|
| BannerText
| The description text shown under the book jacket or format icon in the web client

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/itemstatuses

### Result - Success

|
|

HTTP/1.1 200 OK

<ItemStatusesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage />

<ItemStatusesRows>

<ItemStatusesRow>

<ItemStatusID>1</ItemStatusID>

<Description>In</Description>

<Name>In</Name>

<BannerText>In</BannerText>

</ItemStatusesRow>

<ItemStatusesRow>

<ItemStatusID>2</ItemStatusID>

<Description>Active</Description>

<Name>Active</Name>

<BannerText>Inactive</BannerText>

</ItemStatusesRow>

</ItemStatusesRows>

</ItemStatusesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0