# NotificationUpdate

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceNotificationUpdate.htm_

You are here:

## NotificationUpdate

The NotificationUpdate method will update the notification log and remove or update the notification queue entry. It is also responsible for updating related ItemCheckout data elements and switching phone and text notifications into print notifications. This method should be called after a patron is contacted.

This method supports telephone notification processing as well as email and text messaging for specific types of notices, and may be used in conjunction with the phone notification export process. Telephone notification switches to print for the following failure statuses:

-

7- No dial tone

-

8 - Intercept tones heard

-

9 - Probable bad phone number

-

10 - Maximum number of retries exceeded

-

11 - Undetermined error

A call to AuthenticateStaffUser is required before calling any protected methods. See AuthenticateStaffUser. For more information about protected methods, see PAPI Protected Methods.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/notification/{NotificationTypeID}
|  

### Authorization Required?

Yes

### Protected method?

Yes

### Notification Type ID

|
ID
Notification Type

|
|

0

|

Combined

|
| 1
| 1st Overdue

|
| 2
| Hold

|
| 3
| Cancel

|
| 4
| Recall

|
| 5
| All

|
|

6

|

Route

|
|

7

|

Almost overdue reminder

|
|

8

|

Fine

|
|

9

|

Inactive Reminder

|
|

10

|

Expiration Reminder

|
|

11

|

Bill

|
|

12

|

2nd Overdue

|
|

13

|

3rd Overdue

|
|

14

|

Serial Claim

|
|

15

|

Polaris Fusion Access Request

|
|

16

|

Course Reserves

|
|

17

|

Borrow-By-Mail Failure Notice

|
| 18
| 2nd Hold

|
| 19
| Missing Part

|
| 20
| Manual Bill

### Request Body XML

|
|

<NotificationUpdateData>

<LogonBranchID/>

<LogonUserID/>

<LogonWorkstationID/>

<ReportingOrgID/>

<NotificationStatusID/>

<NotificationDeliveryDate/>

<DeliveryOptionID/>

<DeliveryString/>

<Details/>

<PatronID/>

<PatronLanguageID/>

<ItemRecordID/>

</NotificationUpdateData>

### XML Body Elements

|
| Name
|

Required

|

Description/Notes

|
|

LogonBranchID

|

Yes

|

Logon branch ID

|
|

LogonUserID

|

Yes

|

Logon staff user ID

|
|

LogonWorkstationID

|

Yes

|

Logon workstation ID

|
|

ReportingOrgID

|

See notes

|

Required for text and email notifications. Not required for telephony notification. System ID is automatically used for telephony due to its centralized processing.

|
|

NotificationStatusID

|

Yes

|

Notification Status ID

1 - Call completed – Voice
2 - Call completed - Answering machine
3 - Call not completed - Hang up
4 - Call not completed - Busy
5 - Call not completed - No answer
6 - Call not completed - No ring
7 - Call failed - No dial tone (switches to print)
8 - Call failed - Intercept tones heard (switches to print)
9 - Call failed - Probable bad phone number (switches to print)
10 - Call failed - Maximum number of retries exceeded (switches to print)
11 - Call failed - Undetermined error (switches to print)
12 - Email Completed
13 - Email Failed - Invalid address (switches to print)
14 - Email Failed (switches to print)
15 - Mail Printed

|
|

NotificationDeliveryDate

|

Yes

|

Notification Delivery Date

|
|

DeliveryOptionID

|

Yes

|

Delivery Option ID

1 - Mailing Address
2 - Email Address
3 - Telephone 1
4 - Telephone 2
5 - Telephone 3
6 - FAX
7 - EDI
8 - TXT Messaging

* Only 2, 3, 4, 5, and 8 currently supported.

|
|

DeliveryString

|

Yes

|

Phone number or email

|
|

Details

|

No

|

Status message from notification device.

Manual bill notifications require TxnID in the Details tag.
Cancel hold notifications require RequestID in the Details tag.

|
|

PatronID

|

Yes

|

ID of patron being notified

|
|

PatronLanguageID

|

See notes

|

Language ID used to contact patron. If not supplied, the default will be the patron’s preferred language.

1033 – English
1042 – Korean
1049 – Russian
1066 – Vietnamese
1141 – Hawaiian
2052 – Chinese
3082 – Spanish
3084 – French
12289 – Arabic

|
| ItemRecordID
| See notes
|

ID of item record attached to notification.

Required for overdue and hold notifications. ItemRecordID or ItemBarcode required for hold notices, almost overdue reminders, missing part notices, and bills.

|
|

PatronBarcode

|

 

|

Barcode of the patron being notified.

|
| ItemBarcode
|  
| Barcode of the item patron is being notified about.

### Return Codes

|
|

ID

|

Notification Type

|
|

0

|

Success

|
|

-1

|

Failure general

|
|

-5

|

Failure database

|
|

-6

|

Failure invalid parameter

|
|

-2000

|

Item ID is invalid

|
|

-3000

|

Patron ID is invalid

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

PAPI Error Code

|
|

ErrorMessage

|

Error or information message.

### Example

|
| http://[hostname]/PAPIService/REST/protected/v1/1033/100/1/HfOzmNFbhglFMOQvFpZ
pjzCdM2Bq1Qcs/notification/1

### Body

|
|

<NotificationUpdateData>

<LogonBranchID>1</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1</LogonWorkstationID>

<NotificationStatusID>1</NotificationStatusID>

<NotificationDeliveryDate>2011-08-04</NotificationDeliveryDate>

<DeliveryOptionID>3</DeliveryOptionID>

<DeliveryString>3155551212</DeliveryString>

<Details>Call completed - Voice</Details>

<PatronID>299377</PatronID>

<ItemRecordID>2035574</ItemRecordID>

</NotificationUpdateData>

### Return

|
|

HTTP/1.1 200 OK

<NotificationUpdateResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>NotificationQueue entry does not exist for this delivery option.</ErrorMessage>

</NotificationUpdateResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0