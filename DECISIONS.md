### 001 - Iterative Development: Starting with an MVP
> Status: Accepted

**Context**

We have identified two core features: book management and reading tracking. The full scope of the application has not yet been defined.

**Decision**

We have adopted an iterative development approach with the initial goal of delivering an MVP.

**Rationale**

The main reason for this decision is to avoid implementing features based on unvalidated assumptions.
This approach allows us to get early feedback.

**Consequences**

One potential drawback is the need for modifications and potential rework based on feedback.
One positive consequence is early delivery of a usable version, that allows us to test its functionality, validate the concept before further development and therefore reduce the risk of wasted effort.

---


### 002 - Locking Total Pages After Book Completion
>Status: Accepted

**Context**

The initial design allowed users to modify the total number of pages after a book was marked as *Finished*. This could lead to inconsistencies between the recorded reading progress and the total number of pages.

**Decision**

Once a book is marked as *Finished*, the total number of pages must be locked. Users shall not modify this value.

**Rationale**

The main reason for this decision is to ensure data consistency and maintain data reliability. This decision helps prevent subsequent modifications from distorting reading statistics.

**Consequences**

One positive consequence is the preservation of data consistency. One potential drawback is the inability to correct an error in the total number of pages after book completion.