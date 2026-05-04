# ItemRenew

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceItemRenew.htm_

You are here:

## ItemRenew

Attempt to renew an item that is already checked out.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/itemsout/{ID}
|  

### Authorization required?

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

Barcode of patron.

|
|

ID

|

Yes

|

The item record to be renewed.

### Request Body XML

**Important:** XML elements must be in the order shown below.

|
|

<ItemsOutActionData>

<Action>renew</Action>

<LogonBranchID/>

<LogonUserID/>

<LogonWorkstationID/>

<RenewData>

<IgnoreOverrideErrors/>

</RenewData>

</ItemsOutActionData>

### XML Body Elements

|
|

Name

|

Required

|

Description/Notes

|
|

Action

|

Yes

|

Action to perform on this item checkout record

renew - renew item checkout

|
|

LogonBranchID

|

Yes

|

Current Branch (can default to System [1])

|
|

LogonUserID

|

Yes

|

Current User (can default to PolarisExec)

|
|

LogonWorkstationID

|

Yes

|

Current Workstation (can default to OPACDefault)

|
|

IgnoreOverrideErrors

|

Yes

|

Ignore any errors that can be ignored and if possible, continue processing

### XML Elements Returned

If renewals are successful, a “DueDateRows” node will be present. If the patron has any blocks, a “BlockRows” node will be present.

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
|

PAPIErrorType

|

A PAPI code to tell which 'process' caused the error

1 - Patron block
2 - Item renewal block

|
|

PolarisErrorCode

|

The current error code return via Polaris base processing

|
|

ErrorAllowOverride

|

Does the specific error allow user to override?

|
|

ErrorDesc

|

Block description text.

|
| ItemRecordID
| Item Record ID

|
| DueDate
| The new due date after item renewal successful

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/itemsout/372798

### Body

|
|

<ItemsOutActionData>

<Action>renew</Action>

<LogonBranchID>74</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1</LogonWorkstationID>

<RenewData>

<IgnoreOverrideErrors>true</IgnoreOverrideErrors>

</RenewData>

</ItemsOutActionData>

### Return - Success

|
|

HTTP/1.1 200 OK

<ItemsOutActionResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<ItemRenewResult>

<BlockRows>

<ItemRenewBlockRow>

<PAPIErrorType>2</PAPIErrorType>

<PolarisErrorCode>9999</PolarisErrorCode>

<ErrorAllowOverride>true</ErrorAllowOverride>

<ErrorDesc>This item is overdue. Your account will be charged $4.10</ErrorDesc>

<ItemRecordID>527727</ItemRecordID>

</ItemRenew>

<BlockRow>

</BlockRows>

<DueDateRows>

<ItemRenewDueDateRow>

<ItemRecordID>527727</ItemRecordID>

<DueDate>2009-12-17T23:59:59</DueDate>

</ItemRenewDueDateRow>

</DueDateRows>

</ItemRenewResult>

</ItemsOutActionResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<ItemsOutActionResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-2</PAPIErrorCode>

<ErrorMessage/>

<ItemRenewResult>

<BlockRows>

<ItemRenewBlockRow>

<PAPIErrorType>2</PAPIErrorType>

<PolarisErrorCode>16384</PolarisErrorCode>

<ErrorAllowOverride>false</ErrorAllowOverride>

<ErrorDesc>Item has exceeded renewal limit, not allowed to renew</ErrorDesc>

<ItemRecordID>372798</ItemRecordID>

</ItemRenewBlockRow>

<ItemRenewBlockRow>

<PAPIErrorType>2</PAPIErrorType>

<PolarisErrorCode>9999</PolarisErrorCode>

<ErrorAllowOverride>true</ErrorAllowOverride>

<ErrorDesc>This item is overdue. Your account will be charged $4.20</ErrorDesc>

<ItemRecordID>372798</ItemRecordID>

</ItemRenewBlockRow>

</BlockRows>

<DueDateRows/>

</ItemRenewResult>

</ItemsOutActionResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0