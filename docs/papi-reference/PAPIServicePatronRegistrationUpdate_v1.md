# PatronRegistrationUpdate Version 1

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronRegistrationUpdate_v1.htm_

You are here:

## PatronRegistrationUpdate Version 1

Update patron registration information.

This method supports patron requests to change their registration data, including address, former barcode, language preference, user-defined fields, and others. If this option is set in the Polaris Administration PAC profile **Patron Access Options - Contact info**, **Patron can request address change** and the patron requests a change, an email message confirming the request is sent to the patron. If this option is set in the **Patron Access Options** profile, a verify patron block is placed on the patron record, and an email message is sent to a staff member. An error message (Address change request not permitted, -501) is sent if the **Patron can request address change** option is not set.

**Note:** Incoming phone number formats are validated against customer-defined rules in Polaris System Administration.

|
|  
| PUT
| /public/1 v1/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}
|  

### Authorization required?

Yes

### Public Method?

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

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

Ignoresa

|

No

|

Indicates whether to validate patron update against policies set up in System Administration.

true - Don't check policies, just save the updated information, regardless.

false - Only save patron registration update if data meets system validation checks.

### Request Body XML

|
|

<PatronUpdateData>

<LogonBranchID/>

<LogonUserID/>

<LogonWorkstationID/>

<ReadingListFlag/>

<EmailFormat/>

<DeliveryOptionID/>

<EmailAddress/>

<PhoneVoice1/>

<Password/>

</PatronUpdateData>

### XML Body Elements

|
|

Name

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

Current branch (can default to System [1])

|
|

LogonUserID

|

Yes

|

Current user (can default to PolarisExec)

|
|

LogonWorkstationID

|

Yes

|

Current workstation (can default to OPACDefault)

|
|

ReadingListFlag

|

No

|

Enable or disable reading list

|
|

EmailFormat

|

No

|

Format of email:

1 - Plain text
2 - HTML

|
|

DeliveryOptionID

|

No

|

Delivery options:

0 - None
1 - Mailing address
2 - Email address
3 - Telephone 1
4 - Telephone 2
5 - Telephone 3
6 - FAX
7 - EDI
8 - TXT messaging

|
| DeliveryOption
| No
| ID of how notification should be delivered:

1 - Mailing address
2 - Email address
3 - Phone 1
4 - Phone 2
5 - Phone 3
6 - FAX
7 - EDI
8 - TXT messaging

|
|

EmailAddress

|

No

|

Email address

|
|

AltEmailAddress

|

No

|

Alternate email address

|
|

EnableSMS

|

No

|

Enable additional text messages

0 or False - Do not send additional text notice
1 or True - Send additional text notice

|
| PhoneVoice1
| No
| Primary phone number

|
|

PhoneVoice2

|

No

|

Telephone 2 number

|
|

PhoneVoice3

|

No

|

Telephone 3 number

|
|

Phone1CarrierID

|

No

|

Mobile carrier for Telephone 1

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

Sample list from SA_Mobilephonecarriers table:

1 - AT&T
2 - Bell Canada
8 - Sprint
9 - T_Mobile
10 - Tracfone
11 - Verizon
17 - Boost Mobile
22 - Rogers Canada

|
|

Phone2CarrierID

|

No

|

Mobile carrier for Telephone 2

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

|
|

Phone3CarrierID

|

No

|

Mobile carrier for Telephone 3

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

|
|

TxtPhoneNumber

|

No

|

Mobile number for text messaging:

1 - PhoneVoice1
2 - PhoneVoice2
3 - PhoneVoice3

Unspecified - Indicates no phone number is specified

|
|

EReceiptOptionID

|

No

|

0 - None
2 - Email receipt
8 - Text message receipt

|
|

Password

| No
|

Patron’s password

|
| PatronCode
| No
| Patron code assigned to patron

|
| ExpirationDate
| No
| Patron card expiration date

|
| AddrCheckDate
| No
| Patron's address check date

|
| ExcludeFromAlmostOverdueAutoRenew
| No
| Exclude patron from almost overdue/auto-renew reminder notices

|
| ExcludeFromPatronRecExpiration
| No
| Exclude patron from patron record expiration reminder notices

|
| ExcludeFromInactivePatron
| No
| Exclude from inactive patron reminder notices

|
|

AddressID

| No
| Address ID of requested patron address change

|
|

FreeTextLabel

| No
| Address type label (for example, Home or School) of requested patron address change

|
|

StreetOne

| No
| Patron street one

|
| StreetTwo
| No
| Patron street two

|
| StreetThree
| No
| Patron street three

|
| City
| No
| City of patron address change

|
|

State

| No
|

State of requested patron address change

**Note:** If a *State* field is not required for your country, it can be left unidentified. This requires "StateRequired" to be set to *no* in the System Administration "Countries" table.

|
|

County

| No
| County of requested patron address change

|
|

PostalCode

| No
| Postal code of requested patron address change

|
| ZipPlusFour
| No
| Four digit code added to end of ZIP code

|
|

Country

| No
| Country of the requested patron address change

|
| CountryID
| No
| Country ID of the requested patron address change

|
|

AddressTypeID

| No
|

Address type of requested patron address change:

1 - Generic
2 - Notices

|
| RequestPickupBranchID
| No
| Branch ID of the patron's preferred pickup location for holds

|
| User1
| No
| User-defined field

|
| User2
| No
| User-defined field

|
| User3
| No
| User-defined field

|
| User4
| No
| User-defined field

|
| User5
| No
| User-defined field

|
| LanguageID
| No
| Patron's language preference

|
| FormerID
| No
| Patron's former barcode

|
| NameFirst
| No
| Patron's first name

|
| NameLast
| No
| Patron's last name

|
| NameMiddle
| No
| Patron's middle name

|
| LegalNameFirst
| No
| Patron's legal first name

|
| LegalNameLast
| No
| Patron's legal last name

|
| LegalNameMiddle
| No
| Patron's legal middle name

|
| UseLegalNameOnNotices
| No
| Use patron's legal name on any notices

|
| Birthdate
| No
| Patron's birth date

|
| GenderID
| No
| Patron's selected gender ID

|
| UserName
| No
| Patron's username

|
| Barcode
| No
| Patron's barcode

|
| PatronBranchID
| No
| Patron's Registered branch ID

|
| StatisticalClassID
| No
| Patron's statistical class code ID

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

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022

### Body

|
|

<PatronUpdateData>

<LogonBranchID>1</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1</LogonWorkstationID>

<ReadingListFlag>1</ReadingListFlag>

<EmailFormat>2</EmailFormat>

<DeliveryOptionID>3</DeliveryOptionID>

<EmailAddress>dude@hotmail.com</EmailAddress>

<PhoneVoice1>315-555-3188</PhoneVoice1>

<Password>12345</Password>

<User1>2</User1>

<User2>100</User2>

<User3>10</User3>

<User4>1234</User4>

<User5>Bobby</User5>

<LanguageID>2</LanguageID>

<FormerID>OldBarcode</FormerID>

</PatronUpdateData>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronUpdateResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronUpdateResult>

### Return - Failed

|
|

HTTP/1.1 401 Unauthorized

WWW-Authenticate: PWS realm="Polaris API"

### Error Messages

|
Code
Description

|
| -200
| Invalid AddressID

|
| -221
| PostalCodes insert failed

|
| -222
| Invalid PostalCodeLength

|
| -223
| Invalid PostalCodeFormat

|
| -501
| Patron personal information change is not allowed

|
| -3000
| Invalid PatronID specified

|
| -3400
| PatronAddresses insert failed

|
| -3401
| Invalid AddressType

|
| -3500
| Invalid CountryID

|
| -3501
| Invalid PatronBranchID (Not Defined)

|
| -3502
| Invalid PatronBranchID (Not a Branch)

|
| -3505
| Duplicate Barcode

|
| -3515
| Invalid State (required, but missing)

|
| -3516
| Invalid City

|
| -3517
| Postal Code not found

|
| -3518
| Invalid Email address

|
| -3519
| Invalid DeliveryMethod Value
(No Address for Patron)

|
| -3520
| Invalid delivery method value (No Email Address for Patron)

|
| -3521
| Invalid DeliveryMethod Value
(No PhoneVoice1 for Patron)

|
| -3522
| Invalid DeliveryMethod Value (No PhoneVoice2 for Patron)

|
| -3523
| Invalid DeliveryMethod Value
(No PhoneVoice3 for Patron)

|
| -3524
| Invalid DeliveryMethod Value
(No PhoneFax for Patron)

|
| -3525
| Invalid DeliveryMethod Value

|
| -3526
| Invalid EmailFormat Value

|
| -3527
| Invalid ReadingList Value

|
| -3529
| Duplicate Username

|
| -3532
| Invalid PhoneVoice1

|
| -3533
| Invalid Patron Password Format

|
| -3534
| Invalid Password Length

|
| -3535
| Patron Password Change Is not Allowed

|
| -3536
| Invalid GenderID for the Registered Branch

|
| -3537
| Invalid LegalName Configuration

|
| -3540
| Invalid Birthdate

|
| -3541
| Invalid NameLast Length

|
| -3542
| Invalid NameFirst Length

|
| -3543
| Invalid NameMiddle Length

|
| -3544
| Invalid LegalNameLast Length

|
| -3545
| Invalid LegalNameFirst Length

|
| -3546
| Invalid LegalNameMiddle Length

|
| -3547
| Invalid Username Length

|
| -3548
| Invalid Barcode Length

|
| -3612
| Invalid PatronCodeID

|
| -3613
| Invalid PhoneVoice2

|
| -3614
| Invalid PhoneVoice3

|
| -3615
| Invalid Alt Email Address

|
| -3616
| Invalid TXTPhoneNumber

|
| -3617
| Invalid PhoneCarrier

|
| -3618
| Invalid EReceiptOption

|
| -3619
| Invalid DeliveryMethod No Phone

|
| -3620
| Invalid Email Address for EReceipt

|
| -3622
| Invalid RequestPickupBranchID

|
| -3623
| Invalid User1

|
| -3624
| Invalid User2

|
| -3625
| Invalid User3

|
| -3626
| Invalid User4

|
| -3627
| Invalid User5

|
| -3628
| Invalid LanguageID

|
| -3629
| Invalid FormerID

|
| -3630
| Invalid StatisticalClassID for the registered branch

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0