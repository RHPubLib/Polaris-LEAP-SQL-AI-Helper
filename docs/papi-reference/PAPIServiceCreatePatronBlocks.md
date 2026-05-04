# CreatePatronBlocks

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceCreatePatronBlocks.htm_

You are here:

## CreatePatronBlocks

This protected method creates a block on a patron record. A call to AuthenticateStaffUser is required before calling any protected method. See below for a list of valid block types for patron records. Blocks are de-duplicated on creation. Duplicate blocks are not allowed.

|
|  
| POST
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/patron/{PatronBarcode}/blocks
|  

### Authorization required?

Yes

### Protected?

Yes

### String Query Values

|
| Name
|

Values

|

Required

|

Description/Notes

|
|

PatronBarcode

|

string

|

Yes

|

The patron’s username or barcode

|
| wsid
| >0
| Yes
| ID of the workstation sending this method

### PAPI Error Codes Unique to This Method

|
|

PAPI Error Code

|

Description

|
|

-3506

|

Invalid block value

|
|

-3507

|

Duplicate block value

### Request Body XML

|
|

<CreatePatronBlocksData>

<BlockTypeID />

<BlockValue />

</CreatePatronBlocksData>

### XML Body Elements

|
|

Name

|

Description

|
|

CreatePatronBlocksData

|

A container for the block data

|
|

BlockTypeID

|

The type of block:

1 = Free text block
2 = Library assigned block
3 = System block

|
|

BlockValue

|

The Block value

When a free text block is created - a string no more than 255 characters in length

When a library assigned block is created - an integer representing a valid patron stop ID

When a system block is created - the following integer values are allowed:
64 - Self-Registration from PAC Block
128 - Address update from PAC Block
256 - Express Registration Block
512 - Offline Registration Block

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

PAPI Error code

|
|

ErrorMessage

|

Error or information message

### Example

|
| http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/patron/eric1234/blocks

### Body

|
|

<CreatePatronBlocksData>

<BlockTypeID>1</BlockTypeID>

<BlockValue>A textual block</BlockValue>

</CreatePatronBlocksData>

### Return

|
|

HTTP/1.1 200 OK

<CreatePatronBlocksResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</CreatePatronBlocksResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0