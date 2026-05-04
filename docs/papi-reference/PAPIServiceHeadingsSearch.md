# HeadingsSearch

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHeadingsSearch.htm_

You are here:

## HeadingsSearch

Searches an ordered list of terms and returns headings information relative to a given start point.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/search/headings/{QualifierName}
|  

### Authorization required?

Yes, if authentication level set to ALL

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

Qualifiername

|

Yes

|

Is the qualifier name. Possible values include:

'AU' - Author
'SE' - Series
'SU' - Subject
'TI' - Title

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

startpoint

|

>0

|

No

|

The start point. If there is no matching entry, the first entry with a higher value will be the starting point. Also, if the start point begins with a common leading article (e.g. 'A', 'And' or 'The') and a right-truncated search does not match any entries, then the leading article will be stripped from the start point.

|
|

numterms

|

>0

|

Yes

|

The number of terms requested.

|
|

preferredpos

|

int

|

Yes

|

The preferred position of the start point within the returned entries. If (nPreferredPositionInResponse = 1) then the first row in the returned rowset corresponds to the start point. If (nPreferredPositionInResponse < 1) then the first row in the returned rowset corresponds to the entry N rows beyond the entry corresponding to the start point where N = (ABS(nPreferredPositionInResponse) + 1). If (nPreferredPositionInResponse > 1) then the first row in the returned rowset corresponds to the entry N rows prior to the entry corresponding to the start point where N = (nPreferredPositionInResponse - 1).

|
|

notran

|

>0

|

No

|

Do not record search transaction in the Polaris Transactions database.

### XML Elements Returned

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

Position

|

Is the sequential position of the main heading starting with 1. The first occurrence of a row with a distinct Position value will be the main heading.

|
|

DisplayType

|

Is the heading display type. Possible values include:

0 - Main heading
1 - SEE heading (4xx)
2 - SEE ALSO heading (5xx)

|
|

DisplayConstant

|

Is the display constant associated with the heading. If the heading is a main heading, then this column will be NULL. If the heading is a SEE or SEE ALSO heading, then this column will be non-NULL and the Position column will equal the Position column of the row corresponding to the main heading.

|
|

DisplayTerm

|

Is the display term associated with the heading.

|
|

GlobalOccurrences

|

Is the number of records in which the heading occurs.

|
|

HeadingID

|

Is the heading identifier. The HeadingID is a "Hex String" representation of a 4-byte unsigned integer and corresponds to the HeadingID included in the bibliographic extract file where the Alias name is

999-qualifier_name (e.g. 999-AU, 999-SE, 999-SU, 999-TI).

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/search/headings/SU?startpoint=civil%20war&numterms=10&preferredpos=5

### Return - Success

|
|

<HeadingsSearchResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<HeadingsSearchRows>

<HeadingsSearchRow>

<Position>3</Position>

<DisplayType>0</DisplayType>

<DisplayConstant/>

<DisplayTerm>Civil society--Russia (Federation)</DisplayTerm>

<GlobalOccurrences>1</GlobalOccurrences>

<HeadingID>106D2</HeadingID>

</HeadingsSearchRow>

...

<HeadingsSearchRow>

<Position>6</Position>

<DisplayType>0</DisplayType>

<DisplayConstant/>

<DisplayTerm>Civil war--Drama</DisplayTerm>

<GlobalOccurrences>1</GlobalOccurrences>

<HeadingID>106DC</HeadingID>

</HeadingsSearchRow>

</HeadingsSearchRows>

</HeadingsSearchResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<HeadingsSearchResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Could not execute statement on remote server 'ERMS'.</ErrorMessage>

<HeadingsSearchRows/>

</HeadingsSearchResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0