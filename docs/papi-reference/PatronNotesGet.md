# PatronNotesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronNotesGet.htm_

You are here:

## PatronNotesGet

Retrieves patron notes (blocking and non-blocking), for a given patron barcode.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/notes
|  

### Authorization Required

Yes

### Protected Method

No

### XML elements returned

The following table lists item status elements returned.

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
| Patron Notes
| an object with patron notes details

### Patron Notes Object

|
|

Name

|

Description/Notes

|
| NonBlockingBranchID
|

Non-blocking branch ID

|
| NonBlockOrgName
| Non-blocking organization name

|
| NonBlockingUserID
| Non-blocking user ID

|
| NonBlockUsrName
|

Non-blocking user name

|
| NonBlockingWorkstationID
|

Non-blocking workstation ID

|
| DisplayName
| Non-blocking workstation display name

|
| BlockingBranchID
| Blocking branch ID

|
| BlockingOrgName
|

Blocking organization name

|
| BlockingUserID
|

Blocking user ID

|
| BlockingUsrName
| Blocking user name

|
| BlockingWorkstationID
| Blocking workstation ID

|
| BlockingWorkstationDisplayName
|

Blocking workstation display name

|
| NonBlockingStatusNotes
|

Non-blocking status notes

|
| NonBlockingStatusNoteDate
| Non-blocking status notes date

|
| BlockingStatusNotes
| Blocking status notes

|
| BlockingStatusNoteDate
|

Blocking status notes date

### Example

|
|

http://localhost:5000/public/v1/1033/100/5/patron/1000600652993/notes

### Result - Success

|
|

HTTP/1.1 200 OK

<PatronNotesResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronNotes>

<NonBlockingBranchID i:nil="true"/>

<NonBlockOrgName i:nil="true"/>

<NonBlockingUserID i:nil="true"/>

<NonBlockUsrName i:nil="true"/>

<NonBlockingWorkstationID i:nil="true"/>

<DisplayName i:nil="true"/>

<BlockingBranchID i:nil="true"/>

<BlockingOrgName i:nil="true"/>

<BlockingUserID i:nil="true"/>

<BlockingUsrName i:nil="true"/>

<BlockingWorkstationID i:nil="true"/>

<BlockingWorkstationDisplayName i:nil="true"/>

<NonBlockingStatusNotes>Patron record was merged with 1003200021270, on Apr 14 2009 2:09PM. The secondary record has been deleted. Karen's non-blocking note</NonBlockingStatusNotes>

<NonBlockingStatusNoteDate>2009-04-14T14:09:04.96</NonBlockingStatusNoteDate>

<BlockingStatusNotes>Karen's blocking note</BlockingStatusNotes>

<BlockingStatusNoteDate>2009-04-14T14:09:04.96</BlockingStatusNoteDate>

</PatronNotes>

</PatronNotesResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0