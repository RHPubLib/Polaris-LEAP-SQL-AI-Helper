# Polaris API Guide Revision History

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIRevisionHist.htm_

You are here:

# Polaris API Guide Revision History

The following list shows the revision history for the Polaris API Guide starting with the most current revisions:

-

**PatronBasicDataGet** - Polaris 7.7 - Added a note that a barcode that contains a plus symbol (+) will not function correctly. See PatronBasicDataGet.

-

**ItemCheckinPost** - Polaris 7.7 - Added ItemCheckinPost. This endpoint allows you to check in an item as a staff member. See ItemCheckinPost.

-

New versions created - Polaris 7.6 - The following endpoints were split to create a version 1 and version 2:

-

BibGet version 1

-

BibGetByType version 2

-

PatronRegistrationCreate version 1

-

PatronRegistrationCreate version 2

-

PatronRegistrationUpdate version 1

-

PatronRegistrationUpdate version 2

-

**ItemCheckoutPost** - Polaris 7.6 - Modified BibKeywordSearch so that the endpoint honors the Polaris Administration (staff client) setting for the transacting branch **Block the check-out if the item...Is a renewal (API)**. This setting is to prevent Polaris from using a patron's renewals if they accidentally leave an item on the RFID scanner too long.

-

**ILLRequestPost** - Polaris 7.6 - Added ILLRequestPost. This endpoint starts the ILL request process. See ILLRequestPost.

-

**NotificationUpdate** - Polaris 7.6 - Modified NotificationUpdate so that cancellation notices no longer require ItemRecordID in the Details tag. RequestID is still required in the Details tag. See NotificationUpdate.

-

**BibsPost** - Polaris 7.6 - Added BibsPost. Import MARC records to create and overlay bibliographic records in Polaris. An import job is created for each post. By default, Polaris attempts to match the incoming 001 tag to an existing bibliographic record ID. If Polaris finds a match, it modifies the existing record. If Polaris does not find a match, it creates a new bibliographic record. See BibsPost.

-

**BibKeywordSearch** - Polaris 7.6 - Modified BibKeywordSearch so that the "limit" query parameter is no longer restricted to the values returned by the LimitFiltersGet endpoint. See PAPIServiceBibKeywordSearch.

-

**PAPI Overview** - Polaris 7.5 - Added Pickup Area error codes -4019 to -4023. See PAPI Overview.

-

**HoldRequestCreate** - Polaris 7.5 - Modified HoldRequestCreate. Added HoldPickupAreaID to XML Body Elements. Added StatusValue of "10" to XML Elements Returned. This endpoint starts the local hold request process. See HoldRequestCreate.

-

**MultiPartGet** - Polaris 7.5 - Modified MultiPartGet. Added a third type of "Item" to the XML Element, Type. See MultiPartGet.

-

**ItemCheckoutPost** - Polaris 7.5 - Modified ItemCheckoutPost. Added two ItemBlockFlags:

-

16777216 - Patron does not meet the minimum age requirement for the item.

-

33554432 - Patron is blocked from checking out an item because the item has a status of Damaged. See ItemCheckoutPost.

-

**PickupAreasGet** - Polaris 7.5 - Added PickupAreasGet. This endpoint returns a list of valid pickup areas for the branch based on the organization ID. See PickupAreasGet.

-

**PAPI Overview** - Polaris 7.4 - Added Circulation error codes -6101 to -6119. See PAPI Overview.

-

**ItemCheckoutPost** - Polaris 7.4 - Added ItemCheckoutPost. This endpoint allows you to check out an item as a patron. This endpoint automatically tries to renew an item if the specified patron currently has the item checked out. See ItemCheckoutPost.

-

**PAPI Overview** - Polaris 7.4 - Revised the HTTP Request Header > Date Format when using JSON section to add ISO format. See PAPI Overview.

-

**PatronStatisticalClassesGet** - Polaris 7.3 - Added PatronStatisticalClassesGet. This endpoint provides the ability to get a patron's statistical class ID. See PatronStatisticalClassesGet.

-

**HoldRequestCancel** - Polaris 7.3 - Modified HoldRequestCancel. This endpoint cancels a specific hold request or cancels all local hold requests for a specific patron whose hold requests have a status of held (6), library-enabled. Submitting a zero for the RequestID forces a “cancel all” operation.

-

**PatronBasicDataGet** - Polaris 7.3 - Modified PatronBasicDataGet. This endpoint returns both the patron code and patron statistical class values.

-

**PatronRegistrationCreate** - Polaris 7.3 - Modified PatronRegistrationCreateData. This endpoint allows patrons to self-register and generate a barcode, even if a matching patron record exists. This happens only when the SA setting Profiles > PAC > Patron Access Options, self-registration tab has duplicate detection disabled.

- **PatronRegistrationUpdate** - Polaris 7.3 - Modified PatronRegistrationUpdate. This endpoint returns patron registration information such as name, username, and barcode.

-

**PatronRegistrationUpdate** - Polaris 7.2 - Modified PatronRegistrationUpdate. This endpoint provides the following capabilities:

-

supports patron requests to change their address, update their former barcode, and update their language preference.

-

supports a search for the patron's former barcode. See PatronRegistrationUpdate.

-

**PatronBasicDataGet** - Polaris 7.2 - Modified PatronBasicDataGet. This endpoint includes the patron's former barcode in the basic data returned. See PatronBasicDataGet.

-

**PatronRegistrationCreate** - Polaris 7.2 - Modified PatronRegistrationCreate. This endpoint includes the ability to designate a patron's preferred languages by ID. SeePatronRegistrationCreate.

-

**PatronLanguagesGet** - Polaris 7.2 - Added PatronLanguagesGet. This endpoint provides the ability to get a list of a patron's preferred languages. See PatronLanguagesGet.

-

**Api** - Polaris 7.2 - Added **Api**. This endpoint provides the ability to get a precise list of PAPI version numbers. See Api.

-

**PAPI Overview** - Polaris 7.2 - Added KeyedHashAlgorithm key. This key provides the ability to choose from two different hash algorithms: HMACSHA1 and HMACSHA. See PAPI Overview.

-

**PAPI Overview** - Polaris 7.2 - Revised the PAPI and Swagger section to delete the second URL. See PAPI Overview.

-

**PAPI Overview** - Polaris 7.2 - Revised the Appsettings.config section. See PAPI Overview.

-

**PAPI Overview** - Polaris 7.2 - Changed "Appsettings.config" and derivatives to "Appsettings.json" and derivatives. See PAPI Overview.

-

**HoldRequestPickupBranch** - Polaris 7.2. Corrected the name of the endpoint. Previous versions of this guide referred to the endpoint as "UpdatePickupBranchID". See HoldRequestPickupBranch.

-

Polaris 7.1 - Revised and updated the PAPI Overview section.

-

Polaris 7.1 - Added a new Overview for PAPI Public Methods.

-

Polaris 7.1 - Moved PAPI documentation to an online format.

- **PatronBasicDataGet** - Polaris 7.0. Method now does the following:
- returns the patron's blocks in the PatronSystemBlock element. The documentation for PatronBasicDataGet now includes the XML-elements-returned, PatronSystemBlock and its description. See PatronBasicDataGet.
-

includes query string parameters for patron notes and addresses. The documentation for PatronBasicDataGet now includes the new query string parameters. See PatronBasicDataGet.
-

includes five user-defined fields (UDFs) for patrons. The documentation for PatronBasicDataGet now includes the new UDFs. See PatronRegistrationUpdate.

-

**ILLRequestCancel** - Polaris 7.0. This endpoint allows the consumer to cancel Interlibrary Loan (ILL) requests. See ILLRequestCancelPut.

-

**BibGet** - Polaris 7.0. Method has been updated to return the full monograph for UPC in a bibliographic record. See BibGet.

-

**PatronItemsOutGet** - Polaris 7.0. Method has been updated to support excluding econtent records. See PatronItemsOutGet.

-

**Synch_ItemsByBibIDGet** - Polaris 7.0. Method has been updated to support excluding econtent records. See Synch_ItemsByBibIDGet.

-

**UpdatePatronNotesData** - Polaris 7.0. This endpoint provides the ability to prepend, append, or replace staff notes on patrons. See UpdatePatronNotesData.

-

**PatronNotesGet** - Polaris 7.0. This endpoint provides the ability to retrieve patron notes (blocking and non-blocking), for a given patron barcode. See PatronNotesGet.

-

**PatronRegistrationUpdate** - Polaris 7.0. Method has been updated to include five UDFs for patrons. The documentation for PatronBasicDataGet now includes the new UDFs. See PatronRegistrationUpdate.

-

**PatronUdfConfigsGet** - Polaris 7.0. This endpoint returns the possible user-defined values, when UDFs are not configured as free-text. This endpoint also includes information about the system administration configuration of the UDFs. See PatronUdfConfigsGet.

-

**RecordSetRecordsPut** - Polaris 7.0. Method has been updated to add or remove bibliographic, item, or patron records to or from a record set. See RecordSetContentPut.

-

**RecordSetContentGet** - Polaris 7.0. Method has been updated to return a list of records in a bibliographic or item record set as well as a patron record set. See RecordSetRecordsGet.

-

**JobsPurchaseOrdersPut** - Polaris 7.0. This jobs endpoint validates acquisitions line items before creating a purchase order. See JobsPurchaseOrdersPut.

-

**JobsPurchaseOrdersPost** - Polaris 7.0. This jobs endpoint allows you to create a purchase order as a job. See JobsPurchaseOrdersPost.

-

**JobsPurchaseOrdersResultGet** - Polaris 7.0. This jobs endpoint returns acquisitions purchase order job results. See JobsPurchaseOrdersResultGet.

-

**JobsPurchaseOrdersStatusGet** - Polaris 7.0. This jobs endpoint allows you to query the status of your job. See JobsPurchaseOrdersStatusGet.

- **PatronBasicDataGet** - Polaris 6.7. Method has been updated to return the patron's preferred pickup location for holds in the RequestPickupBranchID element. The documentation for PatronBasicDataGet is now updated to include the XML-elements-returned, ExpirationDate and its description. See PatronBasicDataGet.
-

**PatronRegistrationCreate** - Polaris 6.7. Method has been updated to accept the optional RequestPickupBranchID element. This element specifies the patron's preferred pickup location for holds. See PatronRegistrationCreate.
-

**PatronRegistrationUpdate** - Polaris 6.7. Method has been updated to accept the optional RequestPickupBranchID element. This element specifies the patron's preferred pickup location for holds. See PatronRegistrationUpdate.
- **MaterialTypesGet** - Polaris 6.7. Returns a list of all material types in the system. See MaterialTypesGet.
-

**MARCTypeOfMaterialsGet** - Polaris 6.7. Returns a list of all MARC type of materials in the system. See MARCTypeOfMaterialsGet.
- **ItemStatusesGet** - Polaris 6.7. Returns a list of all item statuses in the system. See ItemStatusesGet.
- **SysHoldStatusesGet** - Polaris 6.7. Returns a list of all system hold statuses in the system. See SysHoldStatusesGet.
- **Synch_GetSerialCompressedHoldingsPaged** - Polaris 6.7. Provides serial-holdings data for consumption and display in a third-party, patron-facing system at the branch and system levels (specifically the compressed-holdings data, the location, and the last received issue). See Synch_GetSerialCompressedHoldingsPaged.
- **Synch_GetSerialCompressedHoldingsByID** - Polaris 6.7. Provides serial-holdings data for consumption and display in a third-party patron-facing system based on a list of one or more bibliographic-record and branch-ID pairs (specifically the compressed-holdings data, the location, and the last received issue). See Synch_GetSerialCompressedHoldingsByID.
-

**Synch_GetBibResourceCountsByID** - Polaris 6.7. This endpoint allows the consumer to retrieve the number of linked item records and local hold counts for multiple bibliographic record IDs in the Polaris database. See Synch_GetBibResourceCountsByID.

- Date format updated - Polaris 6.6. The date format for the following methods is now updated to YYYY-MM-DDTHH:MM:SS to support international date and time.
-

Synch_Get UpdatedAuths
-

Synch_GetUpdatedAuthsPaged
-

Synch_GetDeletedAuths
-

Synch_GetDeletedAuthsPaged
-

Synch_GetDeletedBibs
-

Synch_GetDeletedBibsPaged
-

Synch_GetDeletedItems
-

Synch_GetDeletedItemsPaged
-

Synch_GetDeletedPatrons
-

Synch_GetDeletedPatronsPaged
-

Synch_GetUpdatedBibs
-

Synch_GetUpdatedBibsPaged
-

Synch_GetUpdatedItems
-

Synch_GetUpdatedItemsPaged

- **BibKeywordSearch** - Polaris 6.6. The documentation for BibKeywordSearch is now updated to include more XML-elements-returned descriptions and a more accurate Return-Success example. See BibKeywordSearch.

- **PatronBasicDataGet** and **PatronRegistrationCreate** - Polaris 6.5. The use of a patron's legal name is now supported. The legal name fields LegalNameFirst, LegalNameMiddle, LegalNameLast, and UseLegalNameOnNotices have been added to PatronBasicDataGet and PatronRegistrationCreate. PatronBasicDataGet also includes the new field LegalFullName. See PatronBasicDataGet and PatronRegistrationCreate.
- **PatronBasicDataGet**, **PatronRegistrationCreate**, and **PatronRegistrationUpdate** - Polaris 6.5. The *state* address field can now be unidentified, if a country does not require a state definition. This requires "StateRequired" to be set to *no* in the System Administration "Countries" table. See PatronBasicDataGet, PatronRegistrationCreate, and PatronRegistrationUpdate.
- **HoldRequestCancel** - Polaris 6.5. Shipped holds can now be canceled with the status of "1 inactive", "2" active", and "4 pending". If enabled by the library, hold requests with a status of "5 shipped" can also be canceled. See HoldRequestCancel.

- **PatronRegistrationCreate** and **PatronRegistrationUpdate** - Polaris 6.4. Incoming phone number formats are now validated against customer-defined rules in Polaris System Administration. The TxtPhoneNumber parameter now supports "Unspecified" for instances where no phone number is indicated. The parameter StreetThree has been added as optional. The parameters Phone1CarrierID, Phone2CarrierID, and Phone3CarrierID support a value of -2 if the patron's branch has "Notice: Export text message" enabled in System Administration. See PatronRegistrationCreate and PatronRegistrationUpdate.
- **PatronBasicDataGet** - Polaris 6.4. StreetThree has been added to the PatronAddresses return element. See PatronBasicDataGet.
- **SynchBibsByIDGet** - Polaris 6.4. Bibliographic records can now be queried using a single record ID, a comma-delimited list of IDs, or a range of IDs. A new query string parameter, includeItems, is supported when retrieving records. This parameter includes an 852 tag for each item record linked to the bibliographic record. See Synch_BibsByIDGet.

- **Synch_GetBibsPaged** - Polaris 6.3. New endpoint allows a paged extraction of bib record data. See Synch_BibsPagedGet.
- **PickupBranchesGet** - Polaris 6.3. New endpoint returns a list of valid pickup branches based on the organization ID. See PickupBranchesGet.
- **ShelfLocationsGet** - Polaris 6.3. New endpoint returns a list of shelf locations based on the organization ID. See ShelfLocationsGet.
- **ItemUpdateBarcode** - Polaris 6.3. The new parameter *BarcodeOrID* has been implemented that enables a barcode to be updated using either the item ID or the item barcode as an identifier. An additional new parameter, *isBarcode*, specifies whether the identifier used is an item record ID or a barcode. See ItemUpdateBarcode.
- **PatronHoldRequestGet** - Polaris 6.3. A new *CanSuspend* Boolean property has been added that indicates whether a patron’s hold request can be suspended. See PatronHoldRequestsGet.
-

**PatronReadingHistoryClear** - Polaris 6.3. Removes a range of historical reading history entries by specifying their IDs using the new query string parameter *id*. See PatronReadingHistoryClear.

-

Polaris 5.6 release - Updated title page and revised descriptions for methods RecordSetContentPut and RecordSetRecordsGet. Removed references to release 5.2 from descriptions and clarified that the methods are for patron record sets only.

- **Synch_GetDeletedAuthsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetDeletedAuthsPaged.
- **Synch_GetDeletedBibsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetDeletedBibsPaged.
- **Synch_GetDeletedItemsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetDeletedItemsPaged.
- **Synch_GetDeletedPatronsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetDeletedPatronsPaged.
- **Synch_GetUpdatedAuthsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetUpdatedAuthsPaged.
- **Synch_GetUpdatedBibsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetUpdatedBibsPaged.
- **Synch_GetUpdatedItemsPaged** - Polaris 5.5. New "paged" method allows the caller to retrieve the ID list in smaller packets to prevent timeouts when retrieving long lists. See Synch_GetUpdatedItemsPaged.

- **PatronPreferencesGet** - Added note that states when a patron does not have a delivery method, PAPI returns a description of “null” rather than “none”. See PatronPreferencesGet.
- **PatronRegistationCreate** - Revised description for EnableSMS to Enable additional text message and values include 0/1 or False/True. See PatronRegistrationCreate.

- **PAPI uses Swagger** - Polaris 5.2. See PAPI and Swagger.
- **AuthenticatePatron changes** - Polaris 5.2. AuthenticatePatron supports either barcode or username in the XML body Barcode element. The method supports the **PAC override password** and **Enable Patron username** options, as specified in the Polaris Administration PAC profile **Patron Access options - Log In**. See AuthenticatePatron.
- **NotificationUpdate changes** - Polaris 5.2. Method now supports email and text messaging for specific types of notices. Notification types have been added: 2nd Notice (ID=18); Missing Part (ID=19); Manual Bill (ID=20). See NotificationUpdate.
- **PatronHoldRequestsGet changes** - Polaris 5.2. Designation and VolumeNumber are returned if present in the data. PACDisplayNotes (up to 255 characters from the PAC Display Note field) are returned. See PatronHoldRequestsGet.
- **PatronItemsOutGet changes** - Polaris 5.2. Designation and VolumeNumber are returned if present in the data. CanItemBeRenewed (true/false) is returned. See PatronItemsOutGet.
- **PatronRegistrationCreate changes** - Polaris 5.2. XML body elements now include ExpirationDate, AddrCheckDate, and PatronCode. A new error code, Invalid_Patron_Code (-3612) is added. See PatronRegistrationCreate.
- **PatronUpdate changes** - Polaris 5.2. Now supports patron requests to change address. The following XML body elements are added: AltEmail address; EnableSMS; PhoneVoice2; PhoneVoice3; Phone1CarrierID; Phone2CarrierID; Phone3CarriedID; TxtPhoneNumber; EReceiptOptionID (including None); ExcludeFromAlmostOverdueAutoRenew; ExcludeFromPatronRecExpiration; ExcludeFromInactivePatron; ExpirationDate; AddrCheckDate; PatronCodeID; AddressID; FreeTextLabel; StreetOne; State; County; PostalCode; Country; AddressTypeID. Null (none) is now a valid input option for DeliveryOption. You can remove an email address by sending a blank EmailAddress or Altemail address in the request body; for example: **<EmailAddress><\EmailAddress>** would remove whatever was in the record. See PatronBasicDataGet.
- **DatesClosed** - Polaris 5.2. New method returns a list of dates closed by organization. See DatesClosedGet.
- **PatronCodesGetResult** - Polaris 5.2. New method returns a list of valid patron codes. See PatronCodesGetResult.
- **PatronILLRequestsGet** - Polaris 5.2. New method returns a list of ILL requests placed by the specified patron. The list can be filtered by the status of the request. See PatronILLRequestsGet.
- **RecordSetContentPut** - Polaris 5.2. New method adds or removes records from a patron record set. See RecordSetContentPut.
- **RecordSetRecordsGet** - Polaris 5.2. New method returns a list of record IDs in a specified patron record set. See RecordSetRecordsGet.
- **SAMobilePhoneCarriersGetResult** - Polaris 5.2. New method returns content from the SA_MobilePhoneCarriers table for a specified organization, which specifies the mobile phone carrier selections available for patron record phone fields. See SAMobilePhoneCarriersGetResult.
- **HoldRequestPickupBranch** - Polaris 5.2. New method updates the pickup branch for a hold request when the patron requests the change. See HoldRequestPickupBranch.
- **PatronUpdate** - Polaris 5.2. Documentation updated: **PatronCodeID** element changed to **PatronCode**. See PatronRegistrationUpdate.

- **Updated Type of Material (TOM) list** - Polaris 5.1. See Material Format Types.
- **Method to authenticate patron** - Polaris 5.1 SP1. See AuthenticatePatron.

 

 

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0