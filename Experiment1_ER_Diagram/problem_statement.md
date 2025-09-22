# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---
# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="907" height="704" alt="Screenshot 2025-09-22 132353" src="https://github.com/user-attachments/assets/82668043-761d-4ec7-a233-037c8c9f9750" />

### Entities and Attributes

| Entity        | Attributes (PK, FK) |            Notes                        |
|-------------- |---------------------|-----------------------------------------|
|MEMBER         |   MEMBER-ID         | stores details of library books         |
|BOOK           |   BOOK_ID           | Represents books in the library         |
|EVENT          |   EVENT_ID          | Events organized in the library         |
|AUTHOR         |   AUTHOR_ID         | Authors linked with the events/books    |
|CENTRAL_LIBRARY|                     | Act as the main organizing library      |

### Relationships and Constraints

|         Relationship                 | Cardinality |     Participation     |              Notes                           |
|--------------------------------------|------------|----------------------- |----------------------------------------------|
|  organizes (CENTRAL_LIBRARY–EVENT)   |     1:N    |    Total on EVENT side | Library organizes many events                |
|  register (MEMBER–EVENT)             |     M:N    |    Partial             | Members can register for multiple events     |
|  participates (MEMBER–EVENT)         |     M:N    |    Partial             | Members participate in events                |
|  speaks (AUTHOR–EVENT)               |     1:N    |    Partial             | Author may speak in multiple events          |
|  loans (MEMBER–BOOK)                 |     M:N    |    Partial             | A member can borrow many books               |
|  fine (MEMBER–BOOK)                  |     1:1    |    conditional         | Fine imposed if overdue                      |
|  overdue (BOOK–MEMBER via Fine)      |     M:N    |    Partial             | Tracks overdue books                         |
|  reserves (MEMBER–BOOK)              |     M:N    |    Partial             | Members can reserve books                    |
|  fine° (Fine–DueAmount)              |     1:1    |    Total               | Each fine as a due amount                    |

### Assumption

Each Member has a unique MemberID and belongs to one membership type.

Each Book has a unique BookID and can be borrowed by only one member at a time.

Each Author has a unique AuthorID and can write many books or speak in events.

Each Event has a unique EventID and is organized only by the Central Library.

A Member can borrow multiple books, but overdue returns will generate a Fine.

DueAmount stores the payable fine linked to overdue books.

A Member can register and participate in many events.

An Author can be invited to speak in multiple events.




