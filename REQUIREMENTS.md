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




## 3. Non-functional Requirements

> To be defined

## 4. Open Questions

> To be defined



FR-005 – Add Book Notes
BR-003 – Mandatory Discovery Source