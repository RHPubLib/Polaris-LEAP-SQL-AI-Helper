# PatronBasicDataGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronBasicDataGet.htm_

You are here:

## PatronBasicDataGet

Returns basic name, address, circulation counts, holds, interlibrary loan (ILL) requests, system-block messages, account balances, five user-defined fields, and former barcode for a patron.

**Note**:
A barcode that contains a plus symbol (+) will not function correctly. In IIS URL encoding, the plus symbol is automatically converted to a space, and Polaris API endpoints include the patron barcode in the URL.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/basicdata
|  

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

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer that represents the number of rows returned.

|
|

ErrorMessage

|

Error or information message

|
|

PatronID

|

Unique identifier for the patron

|
|

Barcode

|

Patron barcode

|
|

NameFirst

|

Patron's first name

|
|

NameLast

|

Patron's last name

|
|

NameMiddle

|

Patron’s middle name

|
|

PhoneNumber

|

Patron's primary phone number

|
| EmailAddress
| Patron email address

|
|

ItemsOutCount

|

Number of items checked out to the patron

|
|

ItemsOverdueCount

|

Number of overdue items checked out to the patron

|
|

ItemsOutLostCount

|

Number of items in lost status for the patron

|
|

HoldRequestsTotalCount

|

Number of Polaris and ILL hold requests for this patron

|
|

HoldRequestsCurrentCount

|

Number of Polaris and ILL hold requests in the following statuses: ACTIVE, PENDING, INACTIVE, SHIPPED

|
|

HoldRequestsShippedCount

|

Number of Polaris hold requests in SHIPPED status (sent to library for pickup) for this patron

|
|

HoldRequestsHeldCount

|

Number of Polaris hold requests in HELD status (available for pickup) for this patron

|
|

HoldRequestsUnclaimedCount

|

Number of Polaris hold requests in UNCLAIMED status (available for pickup but never picked up) for this patron

|
|

ChargeBalance

|

The charge balance of the patron's account

|
|

CreditBalance

|

The credit balance of the patron's account

|
|

DepositBalance

|

The deposit balance of the patron's account

|
|

NameTitle

|

Patron’s title

|
|

NameSuffix

|

Patron’s suffix (Ph.D, Jr., Sr., for example)

|
|

PhoneNumber2

|

Patron’s phone number 2

|
|

PhoneNumber3

|

Patron’s phone number 3

|
|

Phone1CarrierID

|

Phone 1 carrier ID

|
|

Phone2CarrierID

|

Phone 2 carrier ID

|
|

Phone3CarrierID

|

Phone 3 carrier ID

|
|

CellPhone

|

This field has been deprecated in 4.1. For backwards compatibility, 4.1 will populate this field using the TXT #.

|
|

CellPhoneCarrierID

|

This field has been deprecated in 4.1. For backwards compatibility, 4.1 will populate this field using the TXT #.

|
|

AltEmailAddress

|

Patron’s alternate email address

|
|

BirthDate

|

Patron’s date of birth

|
|

RegistrationDate

|

Original date of registration

|
|

LastActivityDate

|

Date of last activity

|
|

AddrCheckDate

|

Date of next address check

|
|

MessageNewCount

|

Count of new messages

|
|

MessageReadCount

|

Count of unread messages

|
|

PatronOrgID

|

Branch ID where the patron is registered

|
|

PatronCodeID

|

Code assigned to the patron

|
| DeliveryOptionID
|

ID that represents how notices should be delivered to the patron:

1 - Mail
2 - Email
3 - Phone 1
4 - Phone 2
5 - Phone 3
6 - Fax
8 - Text Message

|
|

ExcludeFromAlmostOverdueAutoRenew

| Patron does not have automatic renewals of checked-out items enabled.

|
|

ExcludeFromPatronRecExpiration

|

Exclude patron from report on expired patrons.

|
|

ExcludeFromInactivePatron

|

Exclude patron from report on inactive patrons.

|
| EReceiptOptionID
|

ID that represents how electronic receipts should be delivered to the patron:

2 - Email
3 - Phone 1
4 - Phone 2
5 - Phone 3
8 - Text Message
100 - Email and Text Message

|
|

TxtPhoneNumber

|

Of the three phone numbers on a patron account, indicates which should be used for text messages of receipts

|
|

EmailFormatID

|

Format of notices and receipts sent by email:

1 - Plain text
2 - HTML

|
|

LegalNameFirst

|

Patron's legal first name

|
|

LegalNameLast

|

Patron's legal last name

|
|

LegalNameMiddle

|

Patron's legal middle name

|
| UseLegalNameOnNotices
|

Indicates whether the legal name is used on library print and phone notices

true - Legal name used
false - Legal name not used

|
| LegalFullName
| Patron's legal full name

|
|

PatronAddresses

|

List of patron’s addresses. Only available if the addresses query string value is supplied in the URL as a nonzero value. Example: **/basicdata?addresses=1**

Address fields:

-

AddressID

-

FreeTextLabel

-

StreetOne

-

StreetTwo

-

StreetThree

-

City

-

State

-

County

-

PostalCode

-

ZipPlusFour

-

Country

-

CountryID

-

AddressTypeID

**Note**: If the country does not require a state, the *state* field may be empty.

|
|

ExpirationDate

|

Date that the patron's registration expires.

|
|

RequestPickupBranchID

|

Branch ID of the patron's preferred pickup location for holds

|
|

PatronSystemBlock

|

Returns BlockID and Block description from the database:

-

64 - block is set when patron self-registers via PAC

-

128 - block is set when patron clicks address update from PAC

-

256 - block is set when express registration is done from CheckOut WF

-

512 - block is set when patron is registered offline

-

1024 - block is set when patron account submitted to collection agency

-

2048 - block is set for Registration Renewal

-

4096 - block is set for Patron Registration Fee

|
|

User1

|

Returns the contents of user-defined field 1

|
|

User2

|

Returns the contents of user-defined field 2

|
|

User3

|

Returns the contents of user-defined field 3

|
|

User4

|

Returns the contents of user-defined field 4

|
|

User5

|

Returns the contents of user-defined field 5

|
|

LanguageID

|

Returns the patron's preferred language

|
|

FormerID

|

Returns the patron's former barcode if one exists

|
|

StatisticalClassID

|

Returns the patron's statistical class code ID

### Query String Parameters

|
|

Name

Value
|

Required

|

Description/Notes

|
|

notes

| 0/1
|

No

|

Flag to determine if notes should be included.

0 or null = exclude
1 = include

|
| addresses
| 0/1
|

No

|

Flag to determine if addresses should be included.

0 or null = exclude existing
1 = include

 

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
basicdata?notes=1

### Return Holds and UDFs — Success

|
|

HTTP/1.1 200 OK

<PatronBasicDataGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<PatronBasicData>

<PatronID>358414</PatronID>

<Barcode>barcode123</Barcode>

<NameFirst>John</NameFirst>

<NameLast>Smith</NameLast>

<NameMiddle>R</NameMiddle>

<PhoneNumber>3151234567</PhoneNumber>

<EmailAddress>email@iii.com</EmailAddress>

<ItemsOutCount>1</ItemsOutCount>

<ItemsOverdueCount>1</ItemsOverdueCount>

<ItemsOutLostCount>1</ItemsOutLostCount>

<HoldRequestsTotalCount>6</HoldRequestsTotalCount>

<HoldRequestsCurrentCount>1</HoldRequestsCurrentCount>

<HoldRequestsShippedCount>0</HoldRequestsShippedCount>

<HoldRequestsHeldCount>0</HoldRequestsHeldCount>

<HoldRequestsUnclaimedCount>2</HoldRequestsUnclaimedCount>

<ChargeBalance>3.3000</ChargeBalance>

<CreditBalance>1.0000</CreditBalance>

<DepositBalance>0.0000</DepositBalance>

<NameTitle>Mr.</NameTitle>

<NameSuffix i:nil="true" />

<PhoneNumber2>3151236789</PhoneNumber2>

<PhoneNumber3>3151230987</PhoneNumber3>

<Phone1CarrierID>0</Phone1CarrierID>

<Phone2CarrierID>0</Phone2CarrierID>

<Phone3CarrierID>0</Phone3CarrierID>

<CellPhone i:nil="true" />

<CellPhoneCarrierID>0</CellPhoneCarrierID>

<AltEmailAddress i:nil="true" />

<BirthDate>1979-01-31T00:00:00</BirthDate>

<RegistrationDate>2014-03-03T00:00:00</RegistrationDate>

<LastActivityDate>2020-12-14T15:46:31.19</LastActivityDate>

<AddrCheckDate>2021-03-07T00:00:00</AddrCheckDate>

<MessageNewCount>0</MessageNewCount>

<MessageReadCount>0</MessageReadCount>

<PatronOrgID>3</PatronOrgID>

<PatronCodeID>6</PatronCodeID>

<DeliveryOptionID>3</DeliveryOptionID>

<ExcludeFromAlmostOverdueAutoRenew>false</ExcludeFromAlmostOverdueAutoRenew>

<ExcludeFromPatronRecExpiration>false</ExcludeFromPatronRecExpiration>

<ExcludeFromInactivePatron>false</ExcludeFromInactivePatron>

<EReceiptOptionID>0</EReceiptOptionID>

<TxtPhoneNumber>0</TxtPhoneNumber>

<EmailFormatID>2</EmailFormatID>

<LegalNameFirst>Name</LegalNameFirst>

<LegalNameLast>Identification</LegalNameLast>

<LegalNameMiddle>On</LegalNameMiddle>

<UseLegalNameOnNotices>false</UseLegalNameOnNotices>

<LegalFullName>Identification, Name On</LegalFullName>

<PatronAddresses>

<PatronAddress>

<AddressID>1162971</AddressID>

<FreeTextLabel>Office</FreeTextLabel>

<StreetOne>123 Main St</StreetOne>

<StreetTwo i:nil="true" />

<StreetThree i:nil="true" />

<City>Liverpool</City>

<State>NY</State>

<County></County>

<PostalCode>13090</PostalCode>

<ZipPlusFour i:nil="true" />

<Country>USA</Country>

<CountryID>1</CountryID>

<AddressTypeID>2</AddressTypeID>

</PatronAddress>

</PatronAddresses>

<ExpirationDate>2020-12-02T00:00:00</ExpirationDate>

<RequestPickupBranchID>3</RequestPickupBranchID>

<User1>565433944</User1>

<User2>User2Text</User2>

<User3>1234</User3>

<User4 i:nil="true" />

<User5>Mike</User5>

<LanguageID>1</LanguageID>

<FormerID>OldBarcode</FormerID>

<StatisticalClassID>17</StatisticalClassID>

<PatronNotes i:nil="true" />

<PatronSystemBlocks i:nil="true" />

</PatronBasicData>

</PatronBasicDataGetResult>

### Return System Blocks — Success

|
|

HTTP/1.1 200 OK

<PatronBasicDataGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<PatronBasicData>

<PatronID>357374</PatronID>

<Barcode>PACREG357374</Barcode>

<NameFirst>John</NameFirst>

<NameLast>Smith</NameLast>

<NameMiddle>Edward</NameMiddle>

<PhoneNumber>315-555-3188</PhoneNumber>

<EmailAddress>dude@hotmail.com</EmailAddress>

<PatronOrgID>3</PatronOrgID>

<PatronCodeID>5</PatronCodeID>

<DeliveryOptionID>3</DeliveryOptionID>

<LegalNameLast>smith</LegalNameLast>

<LegalNameMiddle i:nil="true" />

<PatronAddresses i:nil="true" />

<ExpirationDate>2022-08-01T00:00:00</ExpirationDate>

<RequestPickupBranchID>90</RequestPickupBranchID>

<User1 i:nil="true" />

<User2>Previlages</User2>

<User3>udf3</User3>

<User4>123</User4>

<User5>Alice</User5>

<LanguageID>1</LanguageID>

<FormerID>OldBarcode</FormerID>

<StatisticalClassID>17</StatisticalClassID>

<PatronNotes i:nil="true" />

<PatronSystemBlocks>

<PatronSystemBlock>

<BlockID>128</BlockID>

<BlockDescription>Verify patron data - patron request from PAC</BlockDescription>

</PatronSystemBlock>

<PatronSystemBlock>

<BlockID>1024</BlockID>

<BlockDescription>Patron account has been submitted to collection agency: Amsterdam</BlockDescription>

</PatronSystemBlock>

<PatronSystemBlock>

<BlockID>1024</BlockID>

<BlockDescription>Patron account has been submitted to collection agency: Argyle</BlockDescription>

</PatronSystemBlock>

<PatronSystemBlock>

<BlockID>1024</BlockID>

<BlockDescription>Patron account has been submitted to collection agency: Saratoga</BlockDescription>

</PatronSystemBlock><PatronSystemBlock>

<BlockID>1024</BlockID>

<BlockDescription>Patron account has been submitted to collection agency: Schenectady</BlockDescription>

</PatronSystemBlock>

</PatronSystemBlocks>

</PatronBasicData>

</PatronBasicDataGetResult>

### Return Patron Notes — Success

|
|

HTTP/1.1 200 OK

<PatronBasicDataGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronBasicData>

<PatronID>25551</PatronID>

<Barcode>1000600652993</Barcode>

<NameFirst>Rise</NameFirst>

<NameLast>Klein</NameLast>

<NameMiddle>C</NameMiddle>

<PhoneNumber>315-634-1234</PhoneNumber>

<EmailAddress i:nil="true"/>

<ItemsOutCount>0</ItemsOutCount>

<ItemsOverdueCount>0</ItemsOverdueCount>

<ItemsOutLostCount>0</ItemsOutLostCount>

<HoldRequestsTotalCount>0</HoldRequestsTotalCount>

<HoldRequestsCurrentCount>0</HoldRequestsCurrentCount>

<HoldRequestsShippedCount>0</HoldRequestsShippedCount>

<HoldRequestsHeldCount>0</HoldRequestsHeldCount>

<HoldRequestsUnclaimedCount>0</HoldRequestsUnclaimedCount>

<ChargeBalance>6.0000</ChargeBalance>

<CreditBalance>0.0000</CreditBalance>

<DepositBalance>0.0000</DepositBalance>

<NameTitle>Mrs.</NameTitle>

<NameSuffix i:nil="true"/>

<PhoneNumber2>315-634-1234</PhoneNumber2>

<PhoneNumber3 i:nil="true"/>

<Phone1CarrierID>0</Phone1CarrierID>

<Phone2CarrierID>0</Phone2CarrierID>

<Phone3CarrierID>0</Phone3CarrierID>

<CellPhone i:nil="true"/>

<CellPhoneCarrierID>0</CellPhoneCarrierID>

<AltEmailAddress i:nil="true"/>

<BirthDate i:nil="true"/>

<RegistrationDate>1989-08-14T00:00:00</RegistrationDate>

<LastActivityDate>2007-07-25T18:38:46</LastActivityDate>

<AddrCheckDate>2010-07-18T00:00:00</AddrCheckDate>

<MessageNewCount>0</MessageNewCount>

<MessageReadCount>0</MessageReadCount>

<PatronOrgID>23</PatronOrgID>

<PatronCodeID>13</PatronCodeID>

<DeliveryOptionID>1</DeliveryOptionID>

<ExcludeFromAlmostOverdueAutoRenew>true</ExcludeFromAlmostOverdueAutoRenew>

<ExcludeFromPatronRecExpiration>true</ExcludeFromPatronRecExpiration>

<ExcludeFromInactivePatron>true</ExcludeFromInactivePatron>

<EReceiptOptionID>0</EReceiptOptionID>

<TxtPhoneNumber>0</TxtPhoneNumber>

<EmailFormatID>2</EmailFormatID>

<LegalNameFirst i:nil="true"/>

<LegalNameLast i:nil="true"/>

<LegalNameMiddle i:nil="true"/>

<UseLegalNameOnNotices>false</UseLegalNameOnNotices>

<LegalFullName i:nil="true"/>

<PatronAddresses i:nil="true"/>

<ExpirationDate>2021-01-01T00:00:00</ExpirationDate>

<RequestPickupBranchID>23</RequestPickupBranchID>

<User1 i:nil="true"/>

<User2 i:nil="true"/>

<User3 i:nil="true"/>

<User4 i:nil="true"/>

<User5 i:nil="true"/>

<LanguageID>1</LanguageID>

<FormerID>OldBarcode</FormerID>

<StatisticalClassID>17</StatisticalClassID>

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

</PatronBasicData>

</PatronBasicDataGetResult>

### Return — Failed

|
|

HTTP/1.1 200 OK

<PatronBasicDataGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>An error occurred example</ErrorMessage>

<PatronBasicData i:nil="true"/>

</PatronBasicDataGetResult >

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0