# PatronRenewBlocksGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronRenewBlocks.htm_

You are here:

## PatronRenewBlocksGet

This method takes in a Patron ID and returns patron renewal blocks (if any). It also indicates whether the patron is allowed to renew (the blocks may be informational or actual blocks). It is a protected method and staff must authenticate before calling this method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/circulation/patron/{PatronID}/renewblocks
|  

### Authorization required?

Yes

### Protected?

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

PatronID

|

Yes

|

ID of patron.

### XML Elements Returned

The following XML elements are returned.

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

|
| PatronID
| ID of patron

|
| PatronName
| Name of patron

|
| BlockDescription
| A description of why a patron may not be allowed to renew an item.

|
| CanPatronRenew
| A boolean value indicating whether the patron can renew an item.

### Result - Example 1

|
|

HTTP/1.1 200 OK

<RenewBlocksResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<Blocks>

<Block>

<PatronID>137096</PatronID>

<PatronName>Joseph, Sarah </PatronName>

<BlockDescription>This action is not permitted. Please contact the library regarding your account.</BlockDescription>

</Block>

</Blocks>

<CanPatronRenew>false</CanPatronRenew>

</RenewBlocksResult>

### Result - Example 2

|
|

HTTP/1.1 200 OK

<CanPatronRenewResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<Blocks />

<CanPatronRenew >true</ CanPatronRenew>

</CanPatronRenewResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0