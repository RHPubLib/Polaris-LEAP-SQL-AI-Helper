# BibBooleanSearch

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceBibBooleanSearch.htm_

You are here:

## BibBooleanSearch

Returns a list of bibliographic records that match search criteria. For Boolean searches, you may opt to include the SORTBY clause when using the q query string parameter. This returns search results that are sorted in the specified sort order.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/search/bibs/Boolean?q={ccl}&sortby={sortby}
|  

**Note:** The URL query parameter SORTBY should not be supplied if the SORTBY command is in the CCL query. Example:
**/public/1/search/bib/Boolean?q=frog+sortby+PD/sort.descending**

### Authorization required?

Yes, if authentication level set to ALL.

### {ccl}

Common Command Language snippet. Must be URL encoded.

### {sortby}

RELEVANCE|AU|TI|CALL|PD|AU_TI|AU_PD|TI_AU|TI_PD|TI_TOM|PD_AU|PD_TI|CALL_AU|CALL_TI|CALL_PD|

### Query Parameters

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

q

|

string

|

Yes - Keyword without terms and Boolean

|

Terms. Allows for special characters.

Example:

Harry%20Potter
Auto*

|
| sortby
|

string

(in query string parameter)

| No
|

These apply to SORTBY when used in the q string parameter:

RELEVANCE - Relevance

MP/sort.descending - Most Popular
AU - Author
TI - Title
CALL - Call Number
PD/sort.descending - Publication Date Descending
AUTI - Author, then Title
AUPD - Author, then Publication Date Descending
TIAU - Title, then Author
TIPD - Title, then Publication Date Descending
TITOM - Title , then Type of Material
PDAU - Publication Date Descending, then Author
PDTI - Publication Date Descending, then Title
CALLAU - Call Number, then Author
CALLTI - Call Number, then Title
CALLPD - Call Number, then Publication Date Descending

|
|

sortby

|

string

(in CCL string)

|

No

|

These apply to SORTBY when used in the CCL string:

RELEVANCE - Relevance
AU - Author
AU PD/sort.descending - Author, then Publication Date Descending
AU PD/sort.descending TI - Author, then Publication Date Descending, then Title
AU TI - Author, then Title
CALL - Call Number
CALL AU - Call Number, then Author
CALL AU TI - Call Number, then Author, then Title
CALL PD/sort.descending - Call Number, then Publication Date Descending
CALL PD/sort.descending TI - Call Number, then Publication Date Descending, then Title
CALL PD/sort.descending - Call Number, then Publication Date Descending
MP/sort.descending - Most Popular
PD/sort.descending - Publication Date Descending
PD/sort.descending AU - Publication Date Descending, then Author
PD/sort.descending AU TI - Publication Date Descending, then Author, then Title
PD/sort.descending TI - Publication Date Descending, then Title
TI - Title
TI AU - Title, then Author
TI PD/sort.descending - Title, then Publication Date Descending
TI TOM - Title, then Type of Material

|
|

bibsperpage

|

>0

|

 

|

Default is 10

|
|

page

|

int

|

 

|

Default is 1, for first page

|
|

limit

|

string

|

 

|

Partial CCL command. Examples:

TOM=dvd
TOM=dvd AND AB=74

This parameter is no longer restricted to the values returned by the LimitFiltersGet endpoint.

|
|

notran

|

>0

|

 

|

Do not record search transaction in the Polaris Transactions database.

### XML Elements Returned

The following table lists bibliographic record elements returned.

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
| WordList
| A list of a user's search terms.

|
| TotalRecordsFound
| The number of bib records found for the search.

|
|

Position

|

The ordinal position of the record in the returned search results.

|
| ControlNumber
| The Polaris record identifier (id).

|
| Title
| Primary title of the work.

|
| Author
| Primary author of the work.

|
| Publisher
| Publisher of the work.

|
| Edition
| Edition of the work.

|
| PublicationDate
| Year of publication.

|
| ISBN
| The ISBN number of the work.

|
| Description
| Physical description of the work.

|
| WebLink
| URL for website related to the work.

|
| Fiction
|  

|
| TypeOfMaterial
| Numeric id of the Polaris-defined Type of Material code for the work.

|
| PrimaryTypeOfMaterial
|  

|
| CallNumber
| Bibliographic call number of the work.

|
| CourseReserveCount
| For records that are on course reserve, this is the number of copies available.

|
| LocalItemsIn
| Number of items associated with this work at the specified branch with a status of "In".

|
| LocalItemsTotal
| Number of items associated with this work at the specified branch.

|
| SystemItemsIn
| Number of items associated with this work in the system with a status of "In".

|
| SystemItemsTotal
| Number of items associated with this work in the system.

|
| CurrentHoldRequests
| Count of hold requests for this work.

|
| KWIC
| String showing the keywords used in search in context of where they appear in the MARC record.

|
| RetentionStatement
| For serial works, a summary of which issues are retained.

|
| HoldingsStatement
| For serials works, summary of issues.

|
| HoldingsNote
|  

|
| Summary
| The summary description of a work.

|
| OCLC
| Number assigned by OCLC for this bibliographic work.

|
| UPC
| UPC code associated with the work.

|
| TargetAudience
| MARC code for target audience of the work.

|
| Medium
|  

|
| ThumbnailLink
| Optional URL for cover image of a work.

|
| VernacularTitle
| An alternate graphical representation of the title.

|
| VernacularAuthor
| An alternate graphical representation of the author.

|
| VernacularPublisher
| An alternate graphical representation of the publisher.

|
| LocalControlNumber
| Locally assigned id of the work.

|
| Series
|  

|
| SeriesSuggestedQuery
|  

|
| VernacularSeries
| An alternate graphical representation of the series.

### Example

|
|

/public/{version}/{LangID}/{AppID}/{OrgID}/search/bibs/boolean?q=frog+sortby+PD/
sort.descending

/public/{Version}/{LangID}/{AppID}/{OrgID}/search/bibs/boolean?q=frog&sortby=ti

### Return - Success

|
|

HTTP/1.1 200 OK

<BibSearchResult xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage/>

<WordList>roald dahl dvd &#x0;</WordList>

<TotalRecordsFound>9</TotalRecordsFound>

<BibSearchRows>

<BibSearchRow>

<Position>1</Position>

<ControlNumber>675617</ControlNumber>

<Title>Roald Dahl's The BFG (Big friendly giant) [DVD]</Title>

<Author/>

<Publisher>Arlington, VA : A&E Home Video ; New York : Distributed by New Video, [2006]</Publisher>

<Edition/>

<PublicationDate>2006</PublicationDate>

<ISBN>076708988X</ISBN>

<Description>1 videodisc (DVD) (ca. 88 min.) : sd., col. ; 4 3/4 in.</Description>

<WebLink/>

<Fiction/>

<TypeOfMaterial>33181604</TypeOfMaterial>

<PrimaryTypeOfMaterial>33</PrimaryTypeOfMaterial>

<CallNumber>ROAL</CallNumber>

<CourseReserveCount>0</CourseReserveCount>

<LocalItemsIn>0</LocalItemsIn>

<LocalItemsTotal>0</LocalItemsTotal>

<SystemItemsIn>8</SystemItemsIn>

<SystemItemsTotal>13</SystemItemsTotal>

<CurrentHoldRequests>0</CurrentHoldRequests>

<KWIC>

<span> <b>...</b> <b>Roald</b>
<b>Dahl</b>'s The BFG (Big friendly giant) [ <b>DVD</b>] / a Cosgrove Hall Production ; producers, Mark Hall and Brian <b>...</b> </span>

</KWIC>

<RetentionStatement/>

<HoldingsStatement/>

<HoldingsNote/>

<Summary>One night, Sophie is snatched from her bed at Mrs. Clonkers' orphanage by an awesome giant who whisks her away on a magical and funny adventure.</Summary>

<OCLC/>

<UPC>733961758009</UPC>

<TargetAudience/>

<Medium>[DVD]</Medium>

<ThumbnailLink/>

<VernacularTitle/>

<VernacularAuthor/>

<VernacularPublisher/>

<LocalControlNumber/>

<Series/>

<SeriesSuggestedQuery/>

<VernacularSeries/>

</BibSearchRow>

...

</BibSearchRows>

</BibSearchResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

### Notes

Use a boolean search to retrieve titles attached to a headingID.

**http://localhost/PAPIService/REST/public/v1/1033/100/1/search/bibs/boolean?q=MAH%3d67282**

MAH={AuthorHeadingID}

MSH={SubjectHeadingID}

MTE={TitleEntryID}

MSE={SeriesEntryID}

HeadingsSearch returns a hex HeadingID. This must be converted to decimal.

Boolean searches may also be used to construct more complex searches. Example:

AU=Dahl AND TI=Charlie

**http://localhost/PAPIService/REST/public/v1/1033/100/1/search/bibs/boolean?q=AU%3dDahl%20AND%20TI%3dCharlie**

A power search or keyword search transaction is written when the BibSearch method is called.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0