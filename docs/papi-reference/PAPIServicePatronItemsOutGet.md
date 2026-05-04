# PatronItemsOutGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronItemsOutGet.htm_

You are here:

## PatronItemsOutGet

Returns list of items out to the specified patron. The list can be filtered by ALL items out, OVERDUE items only, or LOST items only. Use the "excludeecontent" parameter to choose if econtent is excluded from the result set.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}}/patron/{PatronBarcode}/itemsout/all?excludeecontent=false
|  

|
|  
| GET
| /public/1/patron/{PatronBarcode}//itemsout/overdue?excludeecontent=false
|  

|
|  
| GET
| /public/1/patron/{PatronBarcode}/itemsout/lost?excludeecontent=false
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

Barcode of patron

|
| ID
| Yes
|

Filter the list of patron's items out by status. Enter one of the following values:

"ALL" - All items out
"OVERDUE" - Only overdue items
"LOST" - Only lost items
For entire list of patron's items out, don't include this field.

### Query String Parameters

|
| Name
|

Value

Required
|

Description/Notes

|
|

excludeecontent

|

true/false

| No
|

To exclude econtent records from the result set. Default: false

 

### XML Elements Returned

One or more items checked out to or lost by the patron. The list is sorted in ascending order by due date.

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

ItemID

|

Polaris ID of the item record

|
|

Barcode

|

The item barcode

|
|

BibID

|

The ID of the associated bibliographic record

|
|

FormatID

|

Polaris ID of the type of format (see "Material Format Types" on page 1)

|
|

FormatDescription

|

Format description

|
|

Title

|

Title of the item

|
|

Author

|

Author of the item

|
|

CallNumber

|

Call Number of the item

|
|

CheckOutDate

|

Check Out Date of the item

|
|

DueDate

|

Due Date of the item

|
|

RenewalCount

|

Number of times item has been renewed by this patron. (For LOST items, this value will always be '0').

|
|

RenewalLimit

|

Maximum number of times this item can be renewed by this patron. (For LOST items, this value will always be '0').

|
|

AssignedBranchID

|

Polaris ID of the branch to which the item is assigned.

|
|

AssignedBranchName

|

Name of the branch to which the item is assigned.

|
|

LoaningBranchID

|

Polaris ID of the branch from which the item was checked out.

|
|

LoaningBranchName

|

Name of the branch from which the item was checked out.

|
|

BillingNoticeSent

|

(Boolean value) Was a billing notice sent for this item?

|
|

ReplacementChargeTxnID

|

(Integer value) Patron account transaction ID for a replacement charge (Can be used for accrued fines)

|
|

ProcessingChargeTxnID

|

(Integer value) Patron account transaction ID for a processing charge
(Can be used for accrued fines)

|
|

OverdueChargeTxnID

|

(Integer value) Patron account transaction ID for an overdue charge
(Can be used for accrued fines)

|
|

DisplayInPAC

|

(Boolean value) Is this item displayable to the public?

|
|

ElectronicItem

|

(Boolean value) Is this an electronic item?

|
|

VendorName

|

The vendor name associated with the electronic item

|
|

VendorAccountName

|

The vendor account name associated with the electronic item

|
|

VendorObjectIdentifier

|

The unique ID of the electronic item in the vendor’s repository

|
|

ISBN

|

The ISBNs of the associated bibliographic records

|
|

ISSN

|

The ISSN of the associated bibliographic records

|
|

OCLCNumber

|

The OCLC number of the associated bibliographic records

|
|

UPCNumber

|

The UPC number of the associated bibliographic records

|
| CanItemBeRenewed
| Indicates whether item is renewable

|
| Designation
| Designation, when present.

|
| VolumeNumber
| Volume, when present.

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
itemsout/all

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronItemsOutGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronItemsOutGetRows>

<PatronItemsOutGetRow>

<ItemID>2859638</ItemID>

<Barcode>0000204137301</Barcode>

<BibID>740185</BibID>

<FormatID>1</FormatID>

<FormatDescription>New / Popular Book</FormatDescription>

<Title>iPhone for dummies</Title>

<Author>Baig, Edward.</Author>

<CallNumber>384.53 Bai</CallNumber>

<CheckOutDate>2013-07-01T16:18:55.4</CheckOutDate>

<DueDate>2013-06-03T23:59:00</DueDate>

<RenewalCount>0</RenewalCount>

<RenewalLimit>1</RenewalLimit>

<AssignedBranchID>90</AssignedBranchID>

<AssignedBranchName>Saratoga Springs Public Library</AssignedBranchName>

<LoaningBranchID>3</LoaningBranchID>

<LoaningBranchName>Amsterdam Free Library</LoaningBranchName>

<BillingNoticeSent>false</BillingNoticeSent>

<ReplacementChargeTxnID>0</ReplacementChargeTxnID>

<ProcessingChargeTxnID>0</ProcessingChargeTxnID>

<OverdueChargeTxnID>0</OverdueChargeTxnID>

<DisplayInPAC>true</DisplayInPAC>

<ElectronicItem>false</ElectronicItem>

<VendorName/>

<VendorAccountName/>

<VendorObjectIdentifier/>

<ISBN>9780470174692</ISBN>

<ISSN/>

<OCLCNumber/>

<UPCNumber/>

</PatronItemsOutGetRow>

</PatronItemsOutGetRows>

</PatronItemsOutGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronItemsOutGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid Status ID Filter</ErrorMessage>

<PatronItemsOutGetRows i:nil="true"/>

</PatronItemsOutGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0