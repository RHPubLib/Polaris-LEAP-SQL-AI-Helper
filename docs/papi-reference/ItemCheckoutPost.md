# ItemCheckoutPost

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ItemCheckoutPost.htm_

You are here:

## ItemCheckoutPost

The ItemCheckout endpoint allows you to check out an item as a patron. This endpoint automatically tries to renew an item if the specified patron currently has the item checked out unless the transacting branch has renewals blocked in Polaris Administration (staff client).

|
|  
| POST
|

/public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/itemsout

|

 

### Authorization Required?

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

The patron's barcode.

### Request Body XML

|
|

<ItemCheckoutData>

<ItemBarcode>{barcode}</ItemBarcode>

<LogonBranchID>{organization-id}</LogonBranchID>

<LogonUserID>{user-id}</LogonUserID>

<LogonWorkstationID>{workstation-id}</LogonWorkstationID>

</ItemCheckoutData>

### Request Body XML

|
|

Name

|

Description/Notes

|
| ItemBarcode
|

Barcode of item.

|
| LogonBranchID
| Current branch (can default to System [1]).

|
|

LogonUserID

|

Current user (can default to PolarisExec).

|
|

LogonWorkstationID

|

Current workstation (can default to OPACDefault).

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI error code. Negative values represent errors and are defined here.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message.

|
| ItemRecordID
| The Polaris item record identifier associated with the specified item barcode.

|
| IsRenewal
|

Indicates whether the item was already checked out to the specified patron.

-

true - check out is a renewal

-

false - check out is not a renewal

|
| DueDate
| Due date for returning the item.

|
| ChargeAmount
|

Charge for checking out the item.

If the ChargeAmount > 0 and the PAPIErrorCode is 0 (Success), then the patron was charged the specified amount. Otherwise, the ChargeAmount is informational (in other words, the patron was **not** charged the specified amount if the PAPIErrorCode <> 0).

|
| PatronBlockFlags
|

Patron block reasons.

When the PAPIErrorCode is -6101 (Checkout_Patron_Blocked), the PatronBlockFlags includes one or more of the following bit fields combined with a bitwise OR operation:

-

1 (0x1) - Patron has too many overdue items.

-

2 (0x2) - Patron has too many long overdue items.

-

4 (0x4) - Patron has too many outstanding claims.

-

8 (0x8) - Patron has too many total claims.

-

16 (0x10) - Patron owes more than second-level fine amount.

-

32 (0x20) - Patron has a collection agency block.

-

64 (0x40) - Patron has address check block.

-

128 (0x80) - Patron has verify borrower block.

-

256 (0x100) - Patron has too many lost items.

-

512 (0x200) - Patron code is blocked.

-

1024 (0x400) - Patron has a library assigned block.

-

2048 (0x800) - Patron has a free text block.

-

4096 (0x1000) - Patron has exceeded the money owed block (estimated fines only).

-

8192 (0x2000) - Patron has exceeded the money owed block (current fines + estimated fines).

-

16384 (0x4000) - Check out is limited to patrons assigned to the transacting branch.

-

32768 (0x8000) - Patron account is secured.

|
| ItemBlockFlags
|

Item block reasons.

When the PAPIErrorCode is -6112 (Checkout_Item_Blocked), the ItemBlockFlags includes one or more of the following bit fields combined with a bitwise OR operation:

-

1 (0x1) - Patron has reached the total number of items out for patron type.

-

2 (0x2) - Patron has reached the total number of items permitted for material type.

-

4 (0x4) - Patron has reached the total number of course reserve items for patron type.

-

8 (0x8) - Item status 'Binding' is blocked.

-

16 (0x10) - Item status 'In-Progress' is blocked.

-

32 (0x20) - Item status 'In-Repair' is blocked.

-

64 (0x40) - Item status 'Lost' is blocked.

-

128 (0x80) - Item status 'Missing' is blocked.

-

256 (0x100) - Item status 'On-Order' is blocked.

-

512 (0x200) - Item status 'In-Transit' is blocked.

-

1024 (0x400) - Item status 'Unavailable' is blocked.

-

2048 (0x800) - Item status 'Withdrawn' is blocked.

-

4096 (0x1000) - Item status 'Routed' is blocked.

-

8192 (0x2000) - Item has a free text block.

-

16384 (0x4000) - Item has a library-assigned block.

-

32768 (0x8000) - Item is from another branch.

-

65536 (0x10000) - Item status 'Claim Missing Parts' is blocked.

-

262144 (0x40000) - Item material type is blocked.

-

524288 (0x80000) - Item is held for another patron.

-

1048576 (0x100000) - Item fills a request for another patron.

-

2097152 (0x200000) - Item is already checked out to another patron.

-

4194304 (0x400000) - Item is blocked because there is a charge for checkout.

-

8388608 (0x800000) - Integrated electronic item.

-

16777216 (0x1000000) - Patron does not meet the minimum age requirement for the item.

-

33554432 (0x2000000) - Item status 'Damaged' is blocked.

|
| RenewalBlockFlags
|

Renewal block reasons.

When the PAPIErrorCode is -6119 (Checkout_Renewal_Blocked), the RenewalBlockFlags includes one or more of the following bit fields combined with a bitwise OR operation:

-

1 (0x1) - Patron, or associated patron, has a patron code block.

-

2 (0x2) - Patron, or associated patron, has a library-assigned block.

-

4 (0x4) - Patron, or associated patron, has a free text block.

-

8 (0x8) - Patron, or associated patron, owes more than second level fine amount.

-

16 (0x10) - Patron, or associated patron, has a collection agency block.

-

32 (0x20) - Patron, or associated patron, has verify borrower block.

-

64 (0x40) - Patron, or associated patron, has too many lost items.

-

128 (0x80) - Patron, or associated patron, has too many outstanding claims.

-

256 (0x100) - Patron, or associated patron, has too many total claims.

-

512 (0x200) - Patron registration will expire before item due date.

-

1024 (0x400) - Item has a library-assigned block.

-

2048 (0x800) - Item has a free text block.

-

4096 (0x1000) - Item is already overdue.

-

8192 (0x2000) - Item is already long overdue.

-

16384 (0x4000) - Item renewal limit reached.

-

32768 (0x8000) - Item fills a request for another patron.

-

65536 (0x10000) - Patron, or associated patron, has too many overdue items.

-

131072 (0x20000) - Patron, or associated patron, has too many long overdue items.

-

262144 (0x40000) - Item is not checked out to the patron.

-

524288 (0x80000) - Automatic renewal only.

-

1048576 (0x100000) - Patron account is secured.

|
| MaterialTypeID
| The material type code for item records (see MaterialTypesGet).

|
| SelfCheckMediaTypeID
| Numeric ID for the self-check media type configuration in the system.

|
| IsMagnetic
|

Indicates if the item is affected by magnetic fields

-

true - the item is magnetic

-

false - the item is not magnetic

|
| CanDesensitize
|

Indicates if the item has a security strip that can be desensitized

-

true - the item can be desensitized

-

false - the item cannot be desensitized

|
| DoubleSided
|

Indicates if the item has both a spine and cover magnet to desensitize

-

true - the item has multiple magnets to desensitize

-

false - the item does not have multiple magnets to desensitize

|
| Unlocker
|

Indicates if the item is stored in an AV case or security locker

-

true - the item is stored in a locker, which must be opened after check out

-

false - the item is not stored in a locker

|
| DDM_MediaFormatID
|

For EnvisionWare RFID, this references the Danish Data Model (DDM) format for the item material type.

-

0 - Undefined

-

1 - Book

-

2 - CD/DVD/etc.

-

3 - Magnetic Tape

-

4 - Other

-

5 - Special Handling Required

-

6 - Small Item

|
| Title
| Primary title of the work.

### Example

|
| https://localhost/REST/public/v1/1033/100/1/patron/21756003332022/itemsout

### Body

|
|

<ItemCheckoutData>

<ItemBarcode>0000410443451</ItemBarcode>

<LogonBranchID>99</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1243</LogonWorkstationID>

</ItemCheckoutData>

### Return - Success

|
|

<ItemCheckoutResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<ItemRecordID>2265135</ItemRecordID>

<IsRenewal>false</IsRenewal>

<DueDate>2023-02-06T23:59:59</DueDate>

<ChargeAmount>0</ChargeAmount>

<PatronBlockFlags>0</PatronBlockFlags>

<ItemBlockFlags>0</ItemBlockFlags>

<RenewalBlockFlags>0</RenewalBlockFlags>

<MaterialTypeID>1</MaterialTypeID>

<SelfCheckMediaTypeID>1</SelfCheckMediaTypeID>

<IsMagnetic>false</IsMagnetic>

<CanDesensitize>true</CanDesensitize>

<DoubleSided>true</DoubleSided>

<Unlocker>false</Unlocker>

<DDM_MediaFormatID>1</DDM_MediaFormatID>

<Title>string</Title>

</ItemCheckoutResult>

### Return - Failed

|
|

<ItemCheckoutResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-6112</PAPIErrorCode>

<ErrorMessage>The item cannot be checked out because the item is blocked.</ErrorMessage>

<ItemRecordID>689497</ItemRecordID>

<IsRenewal>false</IsRenewal>

<DueDate i:nil="true" />

<ChargeAmount>0</ChargeAmount>

<PatronBlockFlags>0</PatronBlockFlags>

<ItemBlockFlags>270336</ItemBlockFlags>

<RenewalBlockFlags>0</RenewalBlockFlags>

<MaterialTypeID>27</MaterialTypeID>

<SelfCheckMediaTypeID>0</SelfCheckMediaTypeID>

<IsMagnetic>false</IsMagnetic>

<CanDesensitize>false</CanDesensitize>

<DoubleSided>false</DoubleSided>

<Unlocker>false</Unlocker>

<DDM_MediaFormatID>4</DDM_MediaFormatID>

<Title>string</Title>

</ItemCheckoutResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0