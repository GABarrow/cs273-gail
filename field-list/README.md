# Phase 2 — Field List

## Authors-This is a single subject table to track database users.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| User_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| User_Last_Name | VARCHAR (50) | NOT NULL | - | |
| User_First_Name | VARCHAR (50) | NOT NULL | - | |
| User_Middle | VARCHAR (50) | NULL | - | Not every author uses a middle name |
| User_Email | VARCHAR (254) | NOT NULL | - | UNIQUE |
| User_Phone | VARCHAR (20) | NOT NULL | - | Not INT - Preserves formatting |
| User_Join_Date | DATE | NOT NULL | CURRENT_DATE | Set Automatically on Insert |
| User_Date_of_Birth | DATE  | NOT NULL | - |  |

## Authors-This is a single subject table to track authors.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Author_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Author_Last_Name | VARCHAR (50) | NOT NULL | - | |
| Author_First_Name | VARCHAR (50) | NOT NULL | - | |
| Author_Middle_ | VARCHAR (50) | NULL | - | Not every author uses a middle name |

## Series-This is a single subject table to track series and link them to their authors and books via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Book_Series_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Author_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_Series_Title| TINYTEXT | NOT NULL | - |  |
| Book_Series_Title| TINYTEXT | NULL | - | Not every book series has a series subtitle  |

## Books-This is a single subject table to track books and link them to their authors and series via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Book_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Author_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_Series_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_Title | TINYTEXT| NOT NULL | - |  |
| Book_Sub-Title | TINYTEXT | NULL | - | Not every book a subtitle |
| Book_# | INT SIGNED | NOT NULL | DECIMAL (5,2) | Allows for prequels to be indicated as negative numbers and books written to be placed between two others in the series |
| Book_Publication_Year | INT UNSIGNED | NOT NULL | YEAR | |

## Characters-This is a single subject table to track characters and link them to their books and series via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Character_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Book_Series_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Character_Last_Name | VARCHAR (50) | NULL | - | Not all characters have last names |
| Character_First_Name | VARCHAR (50) | NOT NULL | - | |
| Character_Middle_Name | VARCHAR (50) | NULL | - | Not all characters have middle names |

## Character Title-This is a linking table to track titles, such as king, throne warden, etc. and connect them to their characters via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Character_Title_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Character_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Character_Title_Name| VARCHAR (50) | NOT NULL| - |  |
| Character_Title_Extended_Name| TINYTEXT | NOT NULL| - |  |

## Race-This is a linking table to track race, such as hobbit, elf, etc. and connect them to their characters via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Race_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Character_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Race_Name| VARCHAR (50) | NOT NULL| - |  |
| Race_Description | TINYTEXT | NOT NULL| - |  |

## Relationships-This is a linking table to track relationships between characters via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Relationship_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Character_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Relationship_Name | VARCHAR (50) | NOT NULL| - |  |

## Actions-This is a single subject table to track character actions via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Action_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Character_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Action Name_Name | VARCHAR (50) | NOT NULL| - |  |
| Action_Description | TINYTEXT | NOT NULL| - |  |

## Locations-This is a single subject table to track Location and link them to their books via a foreign key.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Location ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Book_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Location_Name | TINYTEXT | NOT NULL | | |
| Location_Description | TEXT| NOT NULL | | |
| Location_Characteristics | Location Information |  |
| Location_Rating | Rates location according to scale | May need to create rating table/tables |

## Themes-This is a single subject table to track themes and link them to their books via a foreign key.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Theme (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Book_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Theme | TINYTEXT | NOT NULL | | |
| Theme Description | TEXT| NOT NULL | | |


## Calculated Fields (Do NOT Store)-This is not meant to be a table for query, only a list of possible caclulated fields.
| Field | Derivation |
|---|---|
| User_Full_Name | = User_First_Name + User_Middle_Name + Author_Last_Name |
| User_Age | = TODY() - User_Date_of_Birth |
| Author_Full_Name | = Author_First_Name + Author_Middle_Name + Author_Last_Name |
| Character_Full_Name | = Character_First_Name + Character_Middle_Name + Character_Last_Name |
