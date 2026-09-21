# Phase 2 — Field List

## Authors
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Author_ID (PK)| Unique Identifier for Each Author | Some authors have more than one last name.|
| Author_Last | Author Information |  |
| Author_First | Author Information | |
| Author_Middle | Author Middle Initials or Name | Could be an issue as some authors have two middle initials, some go by no middle name, and some go with full middle name. |

## Books
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Book_ID (PK)| Unique identifier for Each Book |  |
| Author_ID (FK)| Link Book to Author | |
| Book_Series_ID (FK)| Link Book to Series |  |
| Book_Title | Book Information |  |
| Book_Sub-Title | Book Information |  |
| Book_# | Placement of book in series ||
| Book_Publication_Date | Date book was published |  |

## Series
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Book_Series_ID (PK)| Unique identifier for Each Book |  |
| Author_ID (FK)| Link Series to Author | |
| Book_ID (FK)| Link Series to Book |  |
| Book_Series | Series Information |  |

## Characters
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Character_ID (PK)| Unique Identifier for Each Character |  |
| Book_Series_ID (FK)| Link Character to Series |  |
| Book_ID (FK)| Link Character to Book |  |
| Character_Last | Character Information |  |
| Character_First | Character Information |  |
| Character_Race | Character Informmation (Elf, hobbit, human, etc.) |  |
| Character_Relationship | Character relationship to other characters | This may be too broad |
| Character_Action |  |  |
| Character_Action_Rating | Rate character actions by scale | May need to calculate? |

## Locations
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Location ID (PK)| Unique Identifier for Each Location |  |
| Book_ID (FK)| Link book to Author |  |
| Location | Location Information |  |
| Location_Description | Location Information |  |
| Location_Characteristics | Location Information |  |
| Location_Rating | Rates location according to scale | May need to create rating table/tables |

## Themes
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Theme (PK)| Primary Key | May need to separate |
| Book_ID (FK)| Link Theme to Book |  |
| Theme | Passage or Book Theme | May need to separate |
| Theme Description | Gives more information about theme |  |


## Calculated Fields (Do NOT Store)
| Field | Derivation |
|---|---|
| Author_Full_Name | = Author_First + Author_Middle + Author_Last |
| Character_Full_Name | = Character_First + Character_Middle + Character_Last |
