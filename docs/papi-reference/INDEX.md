# Polaris PAPI Reference — RHPL local copy

Mirror of the official III Polaris 8.0 PAPI documentation, fetched 2026-05-04 from
<https://documentation.iii.com/polaris/PAPI/current/PAPIService/>.

**135 pages** organized below. Each page is the converted Markdown of the equivalent .htm — original URL is in the file's header.

**Practical note:** PatronRegistrationUpdate (v1 PUT and v2 PATCH) is in the `Patron - Self-Service Updates` section because both require patron PIN-based authentication (AccessSecret from AuthenticatePatron). There is no staff-callable patron-update endpoint in PAPI. See `/var/opt/rhpl/studentupdate/docs/papi-investigation-findings.md` for the full investigation.

## Authentication

- [AuthenticateStaffUser](PAPIServiceAuthenticate.md)
- [AuthenticatePatron](PAPIServiceAuthenticatePatron.md)

## Bibliographic & Search

- [BibsPost](BibsPost.md)
- [MARCTypeOfMaterialsGet](MARCTypeOfMaterialsGet.md)
- [MultipartGet](MultipartGet.md)
- [BibBooleanSearch](PAPIServiceBibBooleanSearch.md)
- [BibGetByType Version 2](PAPIServiceBibGetByType_v2.md)
- [BibGet Version 1](PAPIServiceBibGet_v1.md)
- [BibKeywordSearch](PAPIServiceBibKeywordSearch.md)
- [HeadingsSearch](PAPIServiceHeadingsSearch.md)

## Holds

- [HoldRequestCancel](PAPIServiceHoldRequestCancel.md)
- [HoldRequestCancelAllForPatron](PAPIServiceHoldRequestCancelAllForPatron.md)
- [HoldRequestCreate](PAPIServiceHoldRequestCreate.md)
- [HoldRequestGetList](PAPIServiceHoldRequestGetList.md)
- [HoldRequestPickupBranch](PAPIServiceHoldRequestPickupBranch.md)
- [HoldRequestReply](PAPIServiceHoldRequestReply.md)
- [HoldRequestSuspend](PAPIServiceHoldRequestSuspend.md)
- [HoldRequestSuspendAllForPatron](PAPIServiceHoldRequestSuspendAllForPatron.md)
- [BibHoldingsGet](PAPIServiceHoldingsGet.md)
- [PatronHoldRequestsGet](PAPIServicePatronHoldRequestsGet.md)
- [SysHoldStatusesGet](SysHoldStatusesGet.md)

## ILL Requests

- [ILLRequestCancelPut](ILLRequestCancelPut.md)
- [ILLRequestPost](ILLRequestPost.md)
- [PatronILLRequestsGet](PAPIServicePatronILLRequestsGet.md)

## Items & Circulation

- [ItemCheckinPost](ItemCheckinPost.md)
- [ItemCheckoutPost](ItemCheckoutPost.md)
- [ItemStatusesGet](ItemStatusesGet.md)
- [ItemRenew](PAPIServiceItemRenew.md)
- [ItemRenewAllForPatron](PAPIServiceItemRenewAllForPatron.md)
- [ItemUpdateBarcode](PAPIServiceItemUpdateBarcode.md)
- [RemoteStorageItemsGet](PAPIServiceRemoteStorageItemsGet.md)

## Patron - Self-Service Updates

- [CreatePatronBlocks](PAPIServiceCreatePatronBlocks.md)
- [PatronPreferencesGet](PAPIServicePatronPreferencesGet.md)
- [PatronRegistrationCreate Version 1](PAPIServicePatronRegistrationCreate_v1.md)
- [PatronRegistrationCreate Version 2](PAPIServicePatronRegistrationCreate_v2.md)
- [PatronRegistrationUpdate Version 1](PAPIServicePatronRegistrationUpdate_v1.md)
- [PatronRegistrationUpdate Version 2](PAPIServicePatronRegistrationUpdate_v2.md)
- [PatronUpdateUserName](PAPIServicePatronUpdateUserName.md)

## Patron - Account / Financial

- [PatronAccountCreateCredit](PAPIServicePatronAccountCreateCredit.md)
- [PatronAccountDepositCredit](PAPIServicePatronAccountDepositCredit.md)
- [PatronAccountGet](PAPIServicePatronAccountGet.md)
- [PatronAccountPay](PAPIServicePatronAccountPay.md)
- [PatronAccountPayAll](PAPIServicePatronAccountPayAll.md)
- [PatronAccountRefundCredit](PAPIServicePatronAccountRefundCredit.md)
- [PatronAccountVoid](PAPIServicePatronAccountVoid.md)
- [PatronAccountCreateTitleList](PatronAccountCreateTitleList.md)
- [PatronAccountDeleteTitleList](PatronAccountDeleteTitleList.md)
- [PatronAccountGetTitleLists](PatronAccountGetTitleLists.md)

## Patron - Reading / Title Lists

- [PatronReadingHistoryClear](PAPIServicePatronReadingHistoryClear.md)
- [PatronReadingHistoryGet](PAPIServicePatronReadingHistoryGet.md)
- [PatronSavedSearchesGet](PAPIServicePatronSavedSearchesGet.md)
- [PatronTitleListAddTitle](PatronTitleListAddTitle.md)
- [PatronTitleListCopyAllTitles](PatronTitleListCopyAllTitles.md)
- [PatronTitleListCopyTitle](PatronTitleListCopyTitle.md)
- [PatronTitleListDeleteAllTitles](PatronTitleListDeleteAllTitles.md)
- [PatronTitleListDeleteTitle](PatronTitleListDeleteTitle.md)
- [PatronTitleListGetTitles](PatronTitleListGetTitles.md)
- [PatronTitleListMoveTitle](PatronTitleListMoveTitle.md)

## Patron - Lookups & Info

- [PatronBasicDataGet](PAPIServicePatronBasicDataGet.md)
- [PatronCirculateBlocksGet](PAPIServicePatronCircBlocksGet.md)
- [PatronItemsOutGet](PAPIServicePatronItemsOutGet.md)
- [PatronSearch](PAPIServicePatronSearch.md)
- [PatronValidate](PAPIServicePatronValidate.md)
- [PatronNotesGet](PatronNotesGet.md)

## Notifications & Messages

- [NotificationUpdate](PAPIServiceNotificationUpdate.md)
- [PatronMessageDelete](PAPIServicePatronMessageDelete.md)
- [PatronMessageUpdateStatus](PAPIServicePatronMessageUpdateStatus.md)
- [PatronMessagesGet](PAPIServicePatronMessagesGet.md)

## Jobs & Background

- [JobsPurchaseOrdersPost](JobsPurchaseOrdersPost.md)
- [JobsPurchaseOrdersPut](JobsPurchaseOrdersPut.md)
- [JobsPurchaseOrdersResultGet](JobsPurchaseOrdersResultsGet.md)
- [JobsPurchaseOrdersStatusGet](JobsPurchaseOrdersStatusGet.md)

## Synchronization (Sync*)

- [Synch Methods for 3rd Party Circulation](PAPIServiceSynchCirculation.md)
- [Synch Methods for 3rd Party Discovery Interfaces](PAPIServiceSynchDiscovery.md)
- [SynchTasksCheckin](SynchTasksCheckin.md)
- [SynchTasksCheckout](SynchTasksCheckout.md)
- [SynchTasksExpireCopy](SynchTasksExpireCopy.md)
- [SynchTasksNotifyPatron](SynchTasksNotifyPatron.md)
- [SynchTasksNotifyPatronItem](SynchTasksNotifyPatronIt.md)
- [SynchTasksPullMARCData](SynchTasksPullMARCData.md)
- [Synch_AuthsByIDGet](Synch_AuthsByIDGet.md)
- [Synch_BibReplacementIDGet](Synch_BibReplacementIDGe.md)
- [Synch_BibsByIDGet](Synch_BibsByIDGet.md)
- [Synch_BibsPagedGet](Synch_BibsPagedGet.md)
- [Synch_GetAuthIDList](Synch_GetAuthIDList.md)
- [Synch_GetBibIDList](Synch_GetBibIDList.md)
- [Synch_GetBibResourceCountsByID](Synch_GetBibResourceCountsByID.md)
- [Synch_GetDeletedAuths](Synch_GetDeletedAuths.md)
- [Synch_GetDeletedAuthsPaged](Synch_GetDeletedAuthsPaged.md)
- [Synch_GetDeletedBibs](Synch_GetDeletedBibs.md)
- [Synch_GetDeletedBibsPaged](Synch_GetDeletedBibsPaged.md)
- [Synch_GetDeletedItems](Synch_GetDeletedItems.md)
- [Synch_GetDeletedItemsPaged](Synch_GetDeletedItemsPaged.md)
- [Synch_GetDeletedPatrons](Synch_GetDeletedPatrons.md)
- [Synch_GetDeletedPatronsPaged](Synch_GetDeletedPatronsPaged.md)
- [Synch_GetItemIDList](Synch_GetItemIDList.md)
- [Synch_GetMaxAuthID](Synch_GetMaxAuthID.md)
- [Synch_GetMaxBibID](Synch_GetMaxBibID.md)
- [Synch_GetMaxItemID](Synch_GetMaxItemID.md)
- [Synch_GetSerialCompressedHoldingsByID](Synch_GetSerialCompressedHoldingsByID.md)
- [Synch_GetSerialCompressedHoldingsPaged](Synch_GetSerialCompressedHoldingsPaged.md)
- [Synch_GetSubscriptionsByID](Synch_GetSubscriptionsBy.md)
- [Synch_GetUpdatedBibs](Synch_GetUpdatedBibs.md)
- [Synch_GetUpdatedBibsPaged](Synch_GetUpdatedBibsPaged.md)
- [Synch_GetUpdatedItems](Synch_GetUpdatedItems.md)
- [Synch_GetUpdatedItemsPaged](Synch_GetUpdatedItemsPaged.md)
- [Synch_Get UpdatedAuths](Synch_Get_UpdatedAuths.md)
- [Synch_GetUpdatedAuthsPaged](Synch_Get_UpdatedAuthsPaged.md)
- [Synch_ItemByIDGet](Synch_ItemByIDGet.md)
- [Synch_ItemsByBibIDGet](Synch_ItemsByBibIDGet.md)

## Reference / Lookups

- [MaterialTypesGet](MaterialTypesGet.md)
- [CollectionsGet](PAPIServiceCollectionsGet.md)
- [DatesClosedGet](PAPIServiceDatesClosed.md)
- [LimitFiltersGet](PAPIServiceLimitFiltersGet.md)
- [OrganizationsGet](PAPIServiceOrganizationsGet.md)
- [PatronCodesGet](PAPIServicePatronCodesGet.md)
- [SAMobilePhoneCarriersGetResult](PAPIServiceSAMobilePhoneCarriersGetResult.md)
- [SortOptionsGet](PAPIServiceSortOptionsGet.md)
- [PatronLanguagesGet](PatronLanguagesGet.md)
- [PickupAreasGet](PatronPickupAreasGet.md)
- [PickupBranchesGet](PatronPickupBranchesGet.md)
- [ShelfLocationsGet](PatronShelfLocationsGet.md)
- [PatronStatisticalClassesGet](PatronStatisticalClassesGet.md)
- [PatronUdfConfigsGet](PatronUdfConfigsGet.md)

## Other

- [Api](Api.md)
- [Legal Notices](LegalNotices.md)
- [Polaris API Guide Revision History](PAPIRevisionHist.md)
- [Polaris API - Overview](PAPIServiceOverview.md)
- [PatronRenewBlocksGet](PAPIServicePatronRenewBlocks.md)
- [RecordSetContentPut](PAPIServiceRecordSetContentPut.md)
- [RecordSetRecordsGet](PAPIServiceRecordSetRecordsGet.md)
- [RequestsUpdateStatus](PAPIServiceUpdateRequestStatus.md)
- [Patron_GetBarcodeFromID](Patron_GetBarcodeFromID.md)
- [PAPI Protected Methods](ProtectedMethodsOvw.md)
- [PAPI Public Methods](PublicMethodsOvw.md)
