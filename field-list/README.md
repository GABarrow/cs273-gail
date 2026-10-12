# Phase 2 — Field List

## Users-This is a single subject table to track database users.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| UserID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| UserLastName | VARCHAR (50) | NOT NULL | - | |
| UserFirstName | VARCHAR (50) | NOT NULL | - | |
| UserMiddle | VARCHAR (50) | NULL | - | Not every author uses a middle name |
| UserEmail | VARCHAR (254) | NOT NULL | - | UNIQUE |
| UserPhone | VARCHAR (20) | NOT NULL | - | Not INT - Preserves formatting |
| UserJoinDate | TIMESTAMP | NOT NULL | CURRENT_DATE | on Creation, CHECK that is today or after|
| UserDateofBirth | DATE  | NOT NULL | - |  |

## Authors-This is a single subject table to track authors.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| AuthorID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| AuthorLast | VARCHAR (50) | NOT NULL | - |  |
| AuthorFirst | VARCHAR (50) | NOT NULL | - | |
| AuthorMiddle | VARCHAR (50) | NULL | - | Not every author uses a middle name |

## Series-This is a single subject table to track series and link them to their authors and books via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| SeriesID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| AuthorID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| BookID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| BookSeriesTitle| TINYTEXT | NOT NULL | - |  |
| BookSeriesSubTitle| TINYTEXT | NULL | - | Not every book series has a series subtitle  |

## Books-This is a single subject table to track books and link them to their authors and series via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| BookID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| AuthorID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| BookSeriesID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| BookTitle | TINYTEXT| NOT NULL | - |  |
| BookSub-Title | TINYTEXT | NULL | - | Not every book has a subtitle |
| Book# | DECIMAL (5,2) | NOT NULL | | CHECK (cannot equal 0) |
| BookPublicationYear | INT UNSIGNED | NOT NULL | YEAR | CHECK must be before today|

## Book_Authors-This is a linking table which links books with to multiple authors or one author to multiple books via a composite key.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| BookID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - Composite, auto-assigned |
| AuthorID (PK)| INT UNSIGNED | NULL| AUTO_INCREMENT |PK - Composite, auto-assigned |
| AuthorOrder| INT UNSIGNED | NOT NULL| AUTO_INCREMENT |CHECK (cannot equal 0) | |

## Characters-This is a single subject table to track characters and link them to their books and series via foreign keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Character_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Book_Series_ID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Book_ID (FK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Character_Last_Name | VARCHAR (50) | NULL | - | Not all characters have last names |
| Character_First_Name | VARCHAR (50) | NOT NULL | - | |
| Character_Middle_Name | VARCHAR (50) | NULL | - | Not all characters have middle names |
| Character_Title_Name| VARCHAR (50) | NOT NULL| - |  |
| Character_Title_Extended_Name| TINYTEXT | NOT NULL| - |  |

## Race-This is a single subject table to track race, such as hobbit, elf, etc. and connect them to their characters via foreign keys keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Race_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| Race_Name| VARCHAR (50) | NOT NULL| - | CHECK Status IN (A, B, C))|
| Race_Description | TINYTEXT | NOT NULL| - |  |

## Character_Race-This is a linking table which links characters to multiple races via a composite key.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Race_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - Composite, auto-assigned |
| Character_ID (PK)| INT UNSIGNED | NULL| AUTO_INCREMENT | PK - Composite, auto-assigned |
| RaceOrder| INT UNSIGNED | NOT NULL| AUTO_INCREMENT |CHECK (cannot equal 0) | |

## Relationships-This is a single subject table to track race, such as hobbit, elf, etc. and connect them to their characters via foreign keys keys.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| RelationshipTypeID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - surrogate, auto-assigned |
| RelationshipName| VARCHAR (50) | Not Null| - |  |
| Character_ID (FK)| INT UNSIGNED | NULL| AUTO_INCREMENT | FK - surrogate, auto-assigned |
| Relationship_Name | VARCHAR (50) | NOT NULL| - |  |

## Character_Race-This is a linking table which links characters to multiple races via a composite key.
| Field | Type | Null? | Default | Notes / Constraints |
|---|---|---|---|---|
| Race_ID (PK)| INT UNSIGNED | NOT NULL| AUTO_INCREMENT | PK - Composite, auto-assigned |
| Character_ID (PK)| INT UNSIGNED | NULL| AUTO_INCREMENT | PK - Composite, auto-assigned |
| RaceOrder| INT UNSIGNED | NOT NULL| AUTO_INCREMENT |CHECK (cannot equal 0) | |

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
| Location_Characteristics | TEXT | NOT NULL | |
| Location_Rating | INT UNSIGNED | NOT NULL | CHECK (Cannot be 0)|

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
