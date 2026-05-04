# PatronAccountGetTitleLists

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronAccountGetTitleLists.htm_

You are here:

## PatronAccountGetTitleLists

Returns a list of all title lists in a patron's account.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patronaccountgettitlelists
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

### XML Elements Returned

The following XML elements are returned.

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
| RecordStoreName
| Name of record store

|
| Sorted
|

Numeric code (0 or 1) indicating how a list is sorted.

0 - The titles in a list are not sorted, they're returned in the order they were added to the list.

1 - The list is sorted in some other way, either by author, title, or publication date.

|
| Count
|

Numeric designation indicating the sort type.

0 - The titles in list are not sorted. They're returned in the order they were added to the list.

1 - The list is sorted in some other way, either by author, title, or publication date.

|
| RecordStoreID
| The number of titles in the given saved title list.

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patronaccountgettitlelists

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountGetTitleListsResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronAccountTitleListsRows>

<PatronAccountTitleListsRow>

<RecordStoreName>Books to read</RecordStoreName>

<Sorted>false</Sorted>

<Count>5</Count>

<RecordStoreID>779</RecordStoreID>

</PatronAccountTitleListsRow>

<PatronAccountTitleListsRow>

<RecordStoreName>Favorites</RecordStoreName>

<Sorted>false</Sorted>

<Count>3</Count>

<RecordStoreID>780</RecordStoreID>

</PatronAccountTitleListsRow>

</PatronAccountTitleListsRows>

</PatronAccountGetTitleListsResult>

### Return - Failed

|
|

HTTP/1.1 401 Unauthorized

WWW-Authenticate: PWS realm="Polaris API"

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0