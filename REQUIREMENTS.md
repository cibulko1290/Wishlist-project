## 1. Functional Requirements

### Pin to Top
--- 

#### FR-001: Pin and Unpin Books

The system shall allow a user to pin and unpin books in the Wishlist. When a book is unpinned, it remains in the Wishlist.

#### FR-002: Display Pinned Books

Pinned books shall appear at the top of the Wishlist.

#### FR-003: Pin Limit Notification

The system shall display a notification when a user attempts to exceed the limit of five pinned books.

The system shall prevent a user from pinning another book until one of the currently pinned books is unpinned.

### Book Discovery Sources
---

#### FR-004: Assign Discovery Sources

The system shall allow a user to assign one or more discovery sources from a predefined list and modify or remove assigned discovery sources.
Users shall be able to assign additional sources to an existing book record later.

#### FR-005: Add Book Notes

The system shall allow a user to add a note to a book record. The *Note* field shall be optional free-text. User can edit or remove a note associated with a book record.

### Book Management
---

#### FR-006: Create Book Record

The system shall allow a user to create a new book record in the *Wishlist* section.

#### FR-007: Edit Book Detail

The system shall allow a user to edit an existing book record.

### Reading Status & History
---

#### FR-008: Change Reading Status

The system shall allow a user to change the reading status to an allowed value for an existing book record.

#### FR-009: Reading Status History

The system shall record every status change from previous status to new status and including a timestamp of the change for each status.

#### FR-010: Record Actual Reading Dates

The system shall allow a user to enter or edit reading start and completion dates retroactively.

#### FR-011: View Reading History

The system shall allow a user to view reading history and filter books by reading  status by either *Finished* or *Did Not Finish*.

### Reading Tracking
---

#### FR-012: Record Reading Progress

The system shall allow a user to enter the current page as their reading position.

#### FR-013: Calculate Reading Progress

The system shall automatically calculate reading progress by subtracting the previous reading position from the current reading position.

#### FR-014: Set Initial Reading Position

The system shall allow a user to enter an initial reading position when starting or resuming reading. This baseline is not counted as new reading progress.

#### FR-015: Set Total Pages

The system shall allow a user to enter the total number of pages for an existing book record when starting reading tracking.

#### FR-016: Confirm Book Completion

The system shall detect when the current reading position reaches the total number of pages. The system shall request user confirmation before changing the reading status to *Finished*.

#### FR-017: Record Reading Progress Date

The system shall automatically assign the current date to a new reading progress entry. The system shall allow a user to backdate a reading progress entry.

### Reading Analytics
---

#### FR-018: View Reading Statistics

The system shall allow a user to view reading statistics including total pages read and number of finished books in the selected time period.

#### FR-019: Select Reporting Period

The system shall allow a user to select a reporting period (*weekly*, *monthly*, *yearly*, or *all-time*) to view reading statistics.

#### FR-020: Visualize Reading Progress

The system shall allow a user to visualize reading progress over time for the selected reporting period.

#### FR-021: Reading Activity by Day of Week

The system shall allow  a user to view the total pages read grouped by day of the week for the selected reporting period.

#### FR-022: Calculate Reading Streak

The system shall automatically calculate a reading streak based on consecutive calendar days with positive recorded reading progress.

#### FR-023: View Reading Streak Statistics







## 2. Business Rules

#### BR-001: Pin Limit

A maximum of **five** books can be pinned at a time.

#### BR-002: Automatic Unpinning

The book shall be automatically unpinned when its status changes from *Want to Read* to *Currently Reading*.

#### BR-003: Mandatory Discovery Source

The *Discovery Sources* field is required. 
The system shall prevent the user from saving a book record without at least one discovery source and prompt the user to select one from the predefined list of discovery sources.

#### BR-004: Mandatory Book Title

The *Book Title* field is required.
The system shall prevent the user from saving a book record without a title and prompt the user to enter a book title.

#### BR-005: Optional Book Meradata

The *Author* and *Genre* fields are optional. The book record shall be editable and the system shall allow users to enter these details later.

#### BR-006: Allowed Reading Statuses

Each book record shall have exactly one current reading status from the following values: *Want to Read*, *Currently Reading*, *Finished* and *Did Not Finish*.

#### BR-007: Allowed Status Transitions

A book's reading status may change only through the following transitions:
- *Want to Read* → *Currently Reading*
- *Want to Read* → *Finished*
- *Currently Reading* → *Want to Read*
- *Currently Reading* → *Finished*
- *Currently Reading* → *Did Not Finish*
- *Did Not Finish* → *Currently Reading*

#### BR-008: Reading Date Precision

Reading start and completion dates may be recorded as either an exact date or a month and year only. Date precision depends on the available information.

#### BR-009: Reading Position Validation

The current reading position must be greater than the previously recorded position. The current reading position must not exceed the total number of pages.

#### BR-010: Completion Confirmation

When a user declines completion confirmation, the system shall keep the reading status *Currently Reading* unchanged. The recorded reading position and progress remain saved. When a user later confirms completion, the recorded reading progress must not be counted twice. 

#### BR-011: Finished Book Tracking Lock

Once a book is marked as *Finished*, the system shall allow neither adding new reading progress entries nor modifying the total number of pages.

#### BR-012: Total Pages Modification Validation

A user can modify the total number of pages while the book is marked as *Currently Reading*. The new total number of pages must not be less than the highest recorded reading position.

#### BR-013: Reading Progress Date Validation

The date of entry must not be in the future. The date and the reading position must preserve the chronological order of existing reading progress entries.

#### BR-014: One Progress Entry per Day

Only one reading progress entry per book  per calendar day is allowed. When an entry already exists for the same book and calendar day, the system shall update the existing entry instead of creating a new one.

#### BR-015: Reading Position Correction

The correction of an existing reading position is allowed while the book's reading status is *Currently Reading*. The corrected reading position must preserve the chronological order of existing reading progress entries.










## 3. Non-functional Requirements

> To be defined

## 4. Open Questions

#### OQ-001: Confirming Book Completion Later

How shall the system allow a user to confirm book completion later if the initial confirmation was declined and the last recorded reading position already equals the total number of pages?

>Resolved

**Resolution**: The user can confirm completion later without creating a new reading progress entry.

**Related Requirements**: FR-016, BR-010

#### OQ-002: Daily Reading Progress and Reading Streak

How shall the system distinguish between progress recorded on a specific date and pages actually read on that date when calculating daily reading statistics and Reading Streaks?

> Resolved

**Resolution**: The system assigns reading progress to the date selected by the user. If no other date is selected, the current date is used. Reading statistics and Reading Streaks are calculated using these recorded dates, without attempting to infer reading activity on unrecorded days.

**Related Requirements**: FR-013, FR-017, FR-022, BR-013, BR-014


#### OQ-003: Resuming a Did Not Finish Book

How shall the system preserve historical reading progress entries when a book marked as Did Not Finish is resumed, while ensuring that previously read pages are not counted twice?

