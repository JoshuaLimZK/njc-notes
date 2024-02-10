#computing 
[[Computing]]

# 10 SQL Databases

>[!info] Database
> A database is a collection of related data where all records have the same structure or collection of data stored in an organised or logical manner.

# 10.1 Flat-file Database

A flat-file, in the context of a medium of storing data, is usually a plain-text file or spreadsheet document, where records usually follow a uniform format, but there are no structures for indexing or recognising relationships between records.

# 10.2 Relational Database

> [!info] Table
> Two-dimensional representation of data, **entities**, stored in rows and columns.

>[!info] Relational Database
>A database where data are organised in one or more tables with relationships between them

Record → Row
Field → Column

![[field-record-value.png]]

In general a table in a relational database can described as:
`TABLE_NAME(ATTRIBUTE_1, ATTRIBUTE_2, ...)`

## 10.2.1 Properties of a table

A table in a relational database should follow the following criteria:
- Values are **ATOMIC** → Each entry only contains 1 piece of information
- Fields are equal across all the records
- Rows are unique, no repeated records
- The order of fields is in significant
- The fields should have a unique name

## 10.2.2 Key Fields

In order to uniquely identify records within a table, we use key fields, or keys.

Types of keys:
- **Candidate key** → **Minimal** set of fields that can uniquely identify each record in a table. Should never be NULL.
- **Primary key** → Candidate key most appropriate to become the main key for a table. In table description, it is normally denoted with an underline on the attribute e.g. TABLE_NAME(<u>ATTRIBUTE_1</u>, ATTRIBUTE_2, ...)
- **Secondary key** → Candidate keys that were not chosen to be the primary key. However users often want to search the table via secondary keys. Setting them up is called *indexing*.
- **Composite key** → a combination of 2 or more fields in a table that together is used as a candidate key, where uniqueness is only guaranteed when the fields are combined
- **Foreign key** → field in one table that is a primary key in another table. It allows us to form relationships between the tables. In table description, often denoted using a dashed underline or asterisk

# 10.3 Designing Relational Databases

>[!info] Data redundancy
> The repetition of entries in a database

## 10.3.1 Normalisation

>[!info] Normalisation
>Process of organising tables in a database to reduce data redundancy to prevent inconsistent data.

During normalisation, tables are usually separated into multiple tables, but still linked to each other via keys.

### 10.3.1.1 First Normal Form (1NF)

Requirements:
- All columns atomic → only 1 piece of information per cell
Achieved by:
- Move some of the attributes to a new field or table
- Link the new table to the original table with a foreign key

### 10.3.1.2 Second Normal Form (2NF)

Requirements:
- Has to be in 1NF
- Every non-key attribute must be **fully dependent** on **all** of the primary key. No attribute can be dependent of only part of the primary key.
Achieved by:
- Move the partially dependent attribute to a new table
- Link the new table to the original table with a foreign key

### 10.3.1.3 Third Normal Form (3NF)

Transitive dependency:
let $x$, $y$ and $z$ be attributes in a table
A functional dependency $x \to z$ is transitive if there exists an attribute $y$ such that $x \to y$ and $y \to z$.

Note that $x \to y$ does not imply the converse $y \to x$

Requirements:
- Has to be in 2NF
- Table should not have transitive dependencies between non-key attributes

# 10.4 Entity-Relationship Diagram

To illustrate the relationships between entities, an entity-relationship diagram (E-R diagram) can be used

Entities (Tables) are represented as rectangles:
![/Users/joshualim/Developer/njccomputing/Notes/images/database-entity.png|200](file:///Users/joshualim/Developer/njccomputing/Notes/images/database-entity.png)
Relationships:
- One to one: Single instance of an entity is associated with a single instance of another entity.
![/Users/joshualim/Developer/njccomputing/Notes/images/database-one-to-one.png|300](file:///Users/joshualim/Developer/njccomputing/Notes/images/database-one-to-one.png)
- One to many: Single instance of an entity is associated with multiple instances of a another entity
![/Users/joshualim/Developer/njccomputing/Notes/images/database-one-to-many.png|300](file:///Users/joshualim/Developer/njccomputing/Notes/images/database-one-to-many.png)
- Many to many: Multiple instances of an entity is associated with multiple instances of another entity
![/Users/joshualim/Developer/njccomputing/Notes/images/database-many-to-many.png|300](file:///Users/joshualim/Developer/njccomputing/Notes/images/database-many-to-many.png)

# 10.5 Advantages of relational databases over flat-file

## 10.5.1 Data Storage

| Flat Files                                                         | Relational Database                                                       |
| ------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| Data is stored in multiple files                                   | Data is contained within a single software application                    |
| Data is highly likely to be duplicated and may become inconsistent | Duplication is minimised so the chance of data inconsistency is reduced.  |
| Because of data duplication, vol of data stored is large           | Vol of data is minimised leading to faster searching and sorting of data. | 

## 10.5.2 Program-data independence

| Flat Files                                                                                                                                                      | Relational Database                                                                                                                             |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| When data structures are rewritten, the software must be edited                                                                                                 | Data structures remain the same even when tables are altered. Existing software does not need to be edited when the table design is changed     |
| Viewing the data is governed by different files used to control the data. This makes all views of the data need to be programmed, making it very time-consuming | Queries and reports can be made with simple 'point and click' features or using data manipulation language. Beginners can write queries quickly | 

# 10.6 SQLite Database

**Structured Query Language (SQL)** is the standard language for the operation and management of relational databases. It is a language used to query, insert, update and modify data.

**SQLite** is the version of SQL that we use out of the many versions.

**Storage classes (data types)**:
- `NULL` an empty value
- `INTEGER` used for a signed integer
- `REAL` used for floating point values
- `TEXT` used for a text string
- `BLOB` used for large binary data

SQLite uses the concept of type affinity on fields. This refers to the preferred data type stored in a column. This means that that you can store any type of data in a column with the recommended types, but they are not enforced.

**Type affinities**:
- All the previous data types
- `NUMERIC` A catch-all data type that may contain values from all five storage classes.

To work with databases we should learn the following CRUD operations:
- <u>C</u>reate
- <u>R</U>ead
- <u>U</u>pdate
- <u>D</u>elete

## 10.6.1 DBBrowser for SQLite

DBBrowser is a GUI based software for modifying databases

When we create tables in DBBrowser, we can set certain constraints on columns.

Contraints:
- `NN` Not Null, column cannot have a `NULL` value
- `PK` Primary Key, denotes column as a primary key
- `AI` Auto Increment, Automatically increments value of the attribute for each new record. Works only for integer values.
- `FOREIGN KEY` Sets column as a foreign key from another table.

## 10.6.2 SQLite Statements

### 10.6.2.1 `SELECT`

Used to retrieve data from the database. To select all fields, use `*`

```sql
SELECT <field_name> FROM <table_name> WHERE <condition>
```

We can use `ORDER BY` to sort the records

```sql
SELECT * FROM TABLE ORDER BY FIELD <ASC/DESC>
```

