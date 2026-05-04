# Ghost-Item Report — YS Inventory

Identifies items in Youth collections that should be on the shelf but weren't seen
during inventory and haven't circulated since inventory began. Used to clean up
records for items that have effectively disappeared from the collection.

## Background

Triggered by Juliane's question (May 2026) about whether Polaris could automatically
update inventory dates with last circ activity. PAPI has no inventory endpoint and
RHPL no longer has DB write access, so an automatic update isn't viable. However,
the same goal — identifying items that are unaccounted for — can be answered with
a read-only report against the live database, no inventory-date update required:

| LastInventoryDate | LastCircTransactionDate | Verdict                         |
| ----------------- | ----------------------- | ------------------------------- |
| Recent            | doesn't matter          | Seen on shelf ✓                 |
| Old/null          | Recent                  | Out with patron / circulating ✓ |
| Old/null          | Old/null                | **Ghost item — investigate**    |

Currently checked-out items naturally fall out of the report because their
`LastCircTransactionDate` is recent — no inventory-date update needed for them.

## Before running

- Set `@InventoryStartDate` to the actual day Jessica started scanning. Otherwise
  every item without a recent LastInventoryDate looks like a ghost.
- Confirm the YS collection-ID list still matches `Polaris.Polaris.Collections`.
  Current list captures every collection whose name starts with "Youth"
  (no Teen, no Reference Desk excluded by status, etc.).
- The query filters to `ItemStatusID = 1` (In) — items Polaris thinks are sitting
  on the shelf right now. To also surface items already flagged Missing/Lost for
  review, broaden the status filter.

## Query (SSMS / Leap SQL extension)

```sql
/* Ghost-item report — Youth collections only.
   Items that should be on the shelf but weren't seen during inventory
   and haven't circulated since inventory began. */

DECLARE @InventoryStartDate DATETIME = '2026-04-01';   -- TODO: when Jessica started

SELECT
    cir.Barcode,
    br.BrowseTitle                          AS Title,
    br.BrowseAuthor                         AS Author,
    LTRIM(RTRIM(
        ISNULL(ird.CallNumberPrefix    + ' ', '') +
        ISNULL(ird.ClassificationNumber + ' ', '') +
        ISNULL(ird.CutterNumber        + ' ', '') +
        ISNULL(ird.CallNumberSuffix,        '')
    ))                                       AS CallNumber,
    ist.Description                         AS Status,
    o.Name                                   AS AssignedBranch,
    c.Name                                   AS Collection,
    cir.LastCircTransactionDate,
    ird.LastInventoryDate,
    cir.ItemRecordID
FROM
    Polaris.Polaris.CircItemRecords     cir WITH (NOLOCK)
INNER JOIN
    Polaris.Polaris.ItemRecordDetails   ird WITH (NOLOCK) ON ird.ItemRecordID         = cir.ItemRecordID
INNER JOIN
    Polaris.Polaris.ItemStatuses        ist WITH (NOLOCK) ON ist.ItemStatusID         = cir.ItemStatusID
INNER JOIN
    Polaris.Polaris.BibliographicRecords br WITH (NOLOCK) ON br.BibliographicRecordID = cir.AssociatedBibRecordID
INNER JOIN
    Polaris.Polaris.Organizations         o WITH (NOLOCK) ON o.OrganizationID         = cir.AssignedBranchID
LEFT JOIN
    Polaris.Polaris.Collections           c WITH (NOLOCK) ON c.CollectionID           = cir.AssignedCollectionID
WHERE
    cir.RecordStatusID = 1
AND cir.ItemStatusID  = 1
AND (ird.LastInventoryDate       IS NULL OR ird.LastInventoryDate       < @InventoryStartDate)
AND (cir.LastCircTransactionDate IS NULL OR cir.LastCircTransactionDate < @InventoryStartDate)
AND cir.AssignedCollectionID IN (
    35, 36, 39, 40, 42, 44, 50, 51, 53, 54, 56, 57, 58, 59, 60, 61, 62, 63, 64, 66,
    70, 80, 82, 86, 98, 100, 102, 105, 138, 139, 140
)
ORDER BY
    c.Name, CallNumber;
```

## Find Tool variant

To load results into a Polaris record set for bulk action (e.g., bulk-change to
Missing), strip the SELECT list to `SELECT DISTINCT cir.ItemRecordID` and remove
the ORDER BY. Everything else stays the same.

## YS collection IDs (as of 2026-05-04)

Confirmed against `Polaris.Polaris.Collections`. Excludes Teen (29–34, 71, 74, 78,
95, 108) and the "Youth Local Author" duplicate is intentional — both 138 and 139
exist in the data with the same name (worth flagging to Cataloging).

| ID  | Name                                       |
| --- | ------------------------------------------ |
| 35  | Youth Biography                            |
| 36  | Youth Board Book                           |
| 39  | Youth DVD                                  |
| 40  | Youth Fiction                              |
| 42  | Youth Graphic Novel                        |
| 44  | Youth Illustrated Fiction                  |
| 50  | Youth Magazine                             |
| 51  | Youth Middle School                        |
| 53  | Youth Middle School Talking Book           |
| 54  | Youth Music CD                             |
| 56  | Youth Newbery / Caldecott Collection (Ref) |
| 57  | Youth Non-Fiction                          |
| 58  | Youth Parent Teacher                       |
| 59  | Youth Picture Book                         |
| 60  | Youth Reader                               |
| 61  | Youth Reference                            |
| 62  | Youth Reference Desk                       |
| 63  | Youth Scouting                             |
| 64  | Youth Talking Book                         |
| 66  | Youth World Languages                      |
| 70  | Youth Puppets                              |
| 80  | Youth Pop-Up books                         |
| 82  | Youth Parent Teacher Reference             |
| 86  | Youth 100 Books                            |
| 98  | Youth Buddy Box                            |
| 100 | Youth School Supply Kit                    |
| 102 | Youth Board Game                           |
| 105 | Youth Findaway                             |
| 138 | Youth Local Author                         |
| 139 | Youth Local Author (duplicate name, different ID) |
| 140 | Youth Middle School Graphic Novel          |

## To formalize into the KB

When ready, drop the query as a `.sql` file in `SQL Statements/` (somewhere like
`Inventory/`) so `process-sql-kb.py` picks it up into `collection-management.md`.
