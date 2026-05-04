# PatronReadingHistoryGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronReadingHistoryGet.htm_

You are here:

## PatronReadingHistoryGet

Returns a historical list of items the patron has checked out. The procedure is capable of returning a count of the total number of titles in the patron’s check-out history, a list of all titles in the history, or a specific page of titles of a specified length.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/readinghistory
|  

### HTTP Verb

GET

### Authorization required?

Yes

### URI Parameters

|
|

Name

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

### Query String Parameters

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

page

|

-1, 0, >0*

|

Yes

|

-1 = Return count only

0 = Return ALL rows

> 0 =Start page

|
|

rowsperpage

|

>0

|

Yes

|

Number of rows to return on a page

To retrieve the patron’s entire reading history, pass in the query string: **?rowsperpage=5&page=0**

To retrieve the count of total reading history rows for this patron, use **page=-1**. The entire reading history will not returned. If you want to retrieve the patron’s last ten items without pulling in the entire list, for example, you can use this count to calculate the actual page number needed.

### XML Elements Returned

One or more items checked out to the patron. The list is sorted in ascending order by check-out date.

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

Note: On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

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

Polaris ID of the type of format (see"Material Format Types" on page 1)

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

LoaningBranchID

|

Polaris ID of the branch from which the item was checked out.

|
|

LoaningBranchName

|

Name of the branch from which the item was checked out.

|
| PatronReadingHistoryID
| ID of patron reading history entry

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
readinghistory?page=1&rowsperpage=5

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronReadingHistoryGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>5</PAPIErrorCode>

<ErrorMessage/>

<PatronReadingHistoryGetRows>

<PatronReadingHistoryGetRow>

<ItemID>2254290</ItemID>

<Barcode>123</Barcode>

<BibID>373330</BibID>

<FormatID>34</FormatID>

<FormatDescription>Videotape</FormatDescription>

<Title>My girl 2 [videorecording]</Title>

<Author/>

<CallNumber>VC Fict My</CallNumber>

<CheckOutDate>2008-10-01T14:14:37</CheckOutDate>

<LoaningBranchID>3</LoaningBranchID>

<LoaningBranchName>Amsterdam Free Library</LoaningBranchName>

<PatronReadingHistoryID>56399</PatronReadingHistoryID>

</PatronReadingHistoryGetRow>
...

<PatronReadingHistoryGetRow>

<ItemID>203302</ItemID>

<Barcode>0000203068887</Barcode>

<BibID>308725</BibID>

<FormatID>1</FormatID>

<FormatDescription>Book</FormatDescription>

<Title>Junie B. Jones has a monster under her bed</Title>

<Author>Park, Barbara.</Author>

<CallNumber>J Fict Par</CallNumber>

<CheckOutDate>2009-02-25T11:22:26</CheckOutDate>

<LoaningBranchID>90</LoaningBranchID>

<LoaningBranchName>Saratoga Springs Public Library</LoaningBranchName>

<PatronReadingHistoryID>56625</PatronReadingHistoryID>

</PatronReadingHistoryGetRow>

</PatronReadingHistoryGetRows>

</PatronReadingHistoryGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronReadingHistoryGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid page supplied</ErrorMessage>

<PatronReadingHistoryGetRows i:nil="true"/>

</PatronReadingHistoryGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0