# ItemUpdateBarcode

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceItemUpdateBarcode.htm_

You are here:

## ItemUpdateBarcode

This protected method allows a user to update the barcode for an existing item record or barcode when a barcode is changed or replaced. It writes a 3009 transaction (item record updated), creates an item record history action, and updates the item’s barcode.

**Important:** A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/cataloging/items/{ItemRecordID}/barcode
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

BarcodeOrID

|

Yes

|

The item record ID or barcode for the item that will have its barcode updated.

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

wsid

|

Yes

|

ID of the workstation sending this method

|
| isBarcode
| No
| A nonzero numeric value that indicates whether a barcode is used. If left blank or set to zero, the BarcodeOrID will be treated as an ItemRecordID.

### Request Body XML

**Important:** XML elements must be in the order shown below.

|
|

<ModyItemData>

<TransactionBranchID />

<ItemBarcode/>

</ModyItemData>

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

TransactionBranchID

|

Yes

|

The branch that is updating the item record.

|
|

ItemBarcode

|

Yes

|

The new barcode of the item.

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

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
|

ErrorMessage

|

Error or information message

### Example

|
| https://egraham-r2vm.gisinfosystems.com/Plato-R2PAPIService/REST/protected/v1/1033/100/1/
GgZtGNGWUrsNlNKmMv7hI61jXQIpRJNS/cataloging/items/2384901/barcode

### Body

|
|

<ModyItemData>

<TransactionBranchID>74</TransactionBranchID>

<ItemBarcode>ECG2384901</ItemBarcode>

</ModyItemData>

### Return

|
|

HTTP/1.1 200 OK

<PAPIResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PAPIResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0