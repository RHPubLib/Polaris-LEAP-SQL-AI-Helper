# SortOptionsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceSortOptionsGet.htm_

You are here:

## SortOptionsGet

Returns list of valid sort options.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/sortoptions
|  

### Authorization required?

Yes, if authentication level set to ALL

### XML Elements Returned

|
| Name
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

Code

|

Sort code

|
|

Description

|

Description used to display to user

|
|

Options

|

Sort option used to build CCL

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/74/sortoptions

### Return - Success

|
|

HTTP/1.1 200 OK

<SortOptionsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>16</PAPIErrorCode>

<ErrorMessage/>

<SortOptionsRows>

<SortOptionsRow>

<Code>RELEVANCE</Code>

<Description>Relevance</Description>

<Options>RELEVANCE</Options>

</SortOptionsRow>

...

<SortOptionsRow>

<Code>CALL_PD</Code>

<Description>Call number, then Publication Date</Description>

<Options>CALL, PD DESC</Options>

</SortOptionsRow>

</SortOptionsRows>

</SortOptionsGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<SortOptionsGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid type specified</ErrorMessage>

<SortOptionsRows i:nil="true"/>

</SortOptionsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0