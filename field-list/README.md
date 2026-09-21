# Phase 2 — Field List

## Authors-This is a single subject table to track authors.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Author_ID (PK)| Unique Identifier for Each Author | Some authors have more than one last name.|
| Author_Last | Author Information |  |
| Author_First | Author Information | |
| Author_Middle | Author Middle Initials or Name | Could be an issue as some authors have two middle initials, some go by no middle name, and some go with full middle name. |

## Books-This is a single subject table to track books and link them to their authors and series via foreign keys.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Book_ID (PK)| Unique identifier for Each Book |  |
| Author_ID (FK)| Link Book to Author | |
| Book_Series_ID (FK)| Link Book to Series |  |
| Book_Title | Book Information |  |
| Book_Sub-Title | Book Information |  |
| Book_# | Placement of book in series ||
| Book_Publication_Date | Date book was published |  |

## Series-This is a single subject table to track series and link them to their authors and books via foreign keys.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Book_Series_ID (PK)| Unique identifier for Each Book |  |
| Author_ID (FK)| Link Series to Author | |
| Book_ID (FK)| Link Series to Book |  |
| Book_Series | Series Information |  |

## Characters-This is a single subject table to track characters and link them to their books and series via foreign keys.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Character_ID (PK)| Unique Identifier for Each Character |  |
| Book_Series_ID (FK)| Link Character to Series |  |
| Book_ID (FK)| Link Character to Book |  |
| Character_Last | Character Information |  |
| Character_First | Character Information |  |
| Character_Middle | Character Information |  |
| Character_Race | Character Informmation (Elf, hobbit, human, etc.) |  |
| Character_Relationship | Character relationship to other characters | This may be too broad |
| Character_Action |  |  |
| Character_Action_Rating | Rate character actions by scale | May need to calculate? |

## Locations-This is a single subject table to track Location and link them to their books via a foreign key.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Location ID (PK)| Unique Identifier for Each Location |  |
| Book_ID (FK)| Link book to Author |  |
| Location | Location Information |  |
| Location_Description | Location Information |  |
| Location_Characteristics | Location Information |  |
| Location_Rating | Rates location according to scale | May need to create rating table/tables |

## Themes-This is a single subject table to track themes and link them to their books via a foreign key.
| Field | Why Needed | Notes / Uncertainty |
|---|---|---|
| Theme (PK)| Primary Key | May need to separate |
| Book_ID (FK)| Link Theme to Book |  |
| Theme | Passage or Book Theme | May need to separate |
| Theme Description | Gives more information about theme |  |


## Calculated Fields (Do NOT Store)-This is not meant to be a table for query, only a list of possible caclulated fields.
| Field | Derivation |
|---|---|
| Author_Full_Name | = Author_First + Author_Middle + Author_Last |
| Character_Full_Name | = Character_First + Character_Middle + Character_Last |

Reflection: For this week's homework I indicated which fields were primary keys, added foreign keys to several tables, added the table titles, added more information to the notes/uncertainty column, separated series from the book table to ensure the table held a single subject, changed publication date field to publication year field for simplicity, and added a middle name field for characters and for authors. I did not have any multipart/multivaried fields (see historical image submitted in Canvas) so I did not make those corrections. I also added an additional Calculated Field to my list. This has been a very interesting process as I learn to pick apart various aspects of what I am trying to query, what users may want to query, and how to logically connect the various aspects of the project. I believe I still need to build some tables from two tables. For example, I may create a relationships table and then link the relationships table to the character table into a separate joined table.
