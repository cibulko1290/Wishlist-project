## 1. Functional Requirements

### Pin to Top 

#### FR-001 - Pin and Unpin Books

The system shall allow users to pin and unpin books in the Wishlist. When a book is unpinned, it remains in the Wishlist.

#### FR-002 - Display Pinned Books

Pinned books shall appear at the top of the Wishlist.

#### FR-003 - Pin Limit Notification

The system shall display a notification when the user attempts to exceed the limit of five pinned books.

The system shall prevent the user from pinning another book until one of the currently pinned books is unpinned.

### Book Discovery Sources

#### FR-004 - Assign Discovery Sources

The system shall allow users to assign one or more discovery sources from a predefined list and modify or remove assigned discovery sources.
Users shall be able to assign additional sources to an existing book record later.

#### FR-005 - Add Book Notes

The system shall allow users to add a note to a book record. The note field shall be optional free-text. Users can edit or remove a note associated with a book record.

## 2. Business Rules

#### BR-001 - Pin Limit

A maximum of **five** books can be pinned at a time.

#### BR-002 - Automatic Unpinning

The book shall be automatically unpinned when its status changes from *Want to Read* to *Currently Reading*.

#### BR-003 - Mandatory Discovery Source

The "Discovery Sources" field is required. 
The system shall prevent the user from saving a book record without at least one discovery source and prompt the user to select one from the predefined list of discovery sources.

## 3. Non-functional Requirements

> To be defined

## 4. Open Questions

> To be defined



FR-005 – Add Book Notes
BR-003 – Mandatory Discovery Source