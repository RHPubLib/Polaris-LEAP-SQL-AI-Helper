# BibKeywordSearch

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceBibKeywordSearch.htm_

You are here:

## BibKeywordSearch

Return list of bibliographic records that match the search criteria.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/search/bibs/keyword/{QualifierName}?q={terms}
|  

|
|  
| GET
| /public/1/search/bibs/keyword/{QualifierName}/{terms} [deprecated]
|  

### Authorization required?

Yes, if authentication level set to ALL.

### {ccl}

Common Command Language snippet. Must be URL encoded.

### {qualifierName}

KW|TI|AU|SU|NOTE|PUB|GENRE|SE|ISBN|ISSN|LCCN|PN|LC|DD|LOCAL|SUDOC|CODEN|STRN|CN|BC|

### {sortby}

RELEVANCE|AU|TI|CALL|PD|AU_TI|AU_PD|TI_AU|TI_PD|TI_TOM|PD_AU|PD_TI|CALL_AU|CALL_TI|CALL_PD|

### {terms}

Must be URL encoded.

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
| qualifierName
| Yes
|

The type of search being conducted.

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

Yes

Keyword without terms and Boolean

|

Terms that correspond to the specified qualifier name. Allows for special characters.

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

No

|

Default is 10.

|
|

page

|

int

|

No

|

Default is 1, for first page.

|
|

limit

|

string

|

No

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

No

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
| Error or information message.

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
| Returns true (1) if the literary form of the work is cataloged as Fiction.

|
| TypeOfMaterial
| Format of the work based on MARC cataloging (for example, book, audio book, DVD, or music CD).

|
| PrimaryTypeOfMaterial
| Numeric id of the Polaris-defined Type of Material code for the work.

|
| CallNumber
| Bibliographic call number of the work.

|
| CourseReserveCount
| For records that are on course reserve, the number of copies available.

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
| For serial works, summary of issues.

|
| HoldingsNote
| For serial works, note text entered when the serial issue was checked in.

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
| Medium designator used in the MARC title statement.

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
| Identifies the series the work is a part of and provides the sequential designation.

|
| SeriesSuggestedQuery
| Identifies the series the work is a part of.

|
| VernacularSeries
| An alternate graphical representation of the series.

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/3/search/bibs/keyword/au?q=roald%20dahl&sortby=PDTI&limit=TOM%3Ddvd&bibsperpage=2

http://localhost/PAPIService/REST/public/v1/1033/100/3/search/bibs/keyword/au/roald%20dahl?sort=PDTI&limit=TOM%3Ddvd&bibsperpage=2 [deprecated]

### Return - Success

|
|

<?xml version="1.0"?>

<BibSearchResult>

<PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<WordList>string</WordList>

<TotalRecordsFound>1</TotalRecordsFound>

<BibSearchRows>

<Position>1</Position>

<ControlNumber>string</ControlNumber>

<Title>string</Title>

<Author>string</Author>

<Publisher>string</Publisher>

<Edition>string</Edition>

<PublicationDate>string</PublicationDate>

<ISBN>string</ISBN>

<Description>string</Description>

<WebLink>string</WebLink>

<Fiction>string</Fiction>

<TypeOfMaterial>string</TypeOfMaterial>

<PrimaryTypeOfMaterial>1</PrimaryTypeOfMaterial>

<CallNumber>string</CallNumber>

<CourseReserveCount>1</CourseReserveCount>

<LocalItemsIn>1</LocalItemsIn>

<LocalItemsTotal>1</LocalItemsTotal>

<SystemItemsIn>1</SystemItemsIn>

<SystemItemsTotal>1</SystemItemsTotal>

<CurrentHoldRequests>1</CurrentHoldRequests>

<KWIC>string</KWIC>

<RetentionStatement>string</RetentionStatement>

<HoldingsStatement>string</HoldingsStatement>

<HoldingsNote>string</HoldingsNote>

<Summary>string</Summary>

<OCLC>string</OCLC>

<UPC>string</UPC>

<TargetAudience>string</TargetAudience>

<Medium>string</Medium>

<ThumbnailLink>string</ThumbnailLink>

<VernacularTitle>string</VernacularTitle>

<VernacularAuthor>string</VernacularAuthor>

<VernacularPublisher>string</VernacularPublisher>

<LocalControlNumber>string</LocalControlNumber>

<Series>string</Series>

<SeriesSuggestedQuery>string</SeriesSuggestedQuery>

<VernacularSeries>string</VernacularSeries>

</BibSearchRows>

</BibSearchResult>

|
|  

### Return - Failed

|
| HTTP/1.1 200 OK

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0