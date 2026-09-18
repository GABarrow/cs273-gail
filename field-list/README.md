# Phase 2 — Field List

## Data Fields
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Author_ID (PK)| Unique identifier for each author ||
| Author_Last | Author Information |  |
| Author_First | Author Information | |

| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Book_ID (PK)| Link book to author |  |
| Book_Title | Book Information |  |
| Book_Series | Link books to one another and author |  |
| Book_# | Placement of book in series ||
| Publication_Date | Date book was published |  |

| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Character_ID (PK)| Link Character to book(s) |  |
| Character_Last | Character Information |  |
| Character_First | Character Information |  |
| Character_Race | Character Informmation (Elf, hobbit, human, etc.) |  |
| Character_Relationship | Character relationship to other characters | This may be too broad |
| Character_Action |  |  |
| Character_Action_Rating | Rate character actions by scale | May need to calculate? |

| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Location | Location Information |  |
| Location_Description | Location Information |  |
| Location_Characteristics | Location Information |  |
| Location_Rating | Rates location according to scale | May need to create rating table/tables |

| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Theme | Passage or book Theme | May need to separate |
| Theme Description | Gives more information about theme |  |


## Calculated Fields (Do NOT Store)
| Field | Derivation |
|---|---|
| Author_Full_Name | = Author_First + Author_Middle + Author_Last |
