# Database Normalization

## What is Database Normalization
- designing a db schema in such a way that it can't express [redundant](#redundacy) information
- db design principle for organizing data consistently
- usually involves breaking up into several tables linked together with relationships
    - relationships are achieved using [primary keys](#primary-key), [foreign keys](#foreign-key), [composite keys](#composite-key)
- also helps to protect against:
  - insertion [anomalies](#anomalies)
  - update [anomalies](#anomalies)
  - deletion [anomalies](#anomalies)
- You can normalize a db into 1NF, 2NF 3NF, BCNF, 4NF, 5NF
    - Normalization levels are culmulative, they build on each other, 3NF meets 2NF criteria too

## Why we Normalize Databases
- helps avoid [redundancy](#redundancy) 
- helps maintain integrity of db
- organize data in a consistent way
- can eliminate undesirable side effects during insertion, deletion, updating

## Assessment of Database Design

### When should be normalize
- DB Normalization is a scale from 1st NF -> 5NF
- You should selects which normalization you want to acheive based your threat model for [redundant](#redundacy) information and database action [anomalies](#anomalies)
    - 1NF is the most lenient form of normalization and catches the least amound of errors
    - 5NF is the strictest form of normalization and catches the most amount of errors

# Database Normalization Levels

## First Normal Form (1NF)
**Why we need it:**
- Eliminates [repeating groups](#repeating-groups)
- Ensures atomic values

**Criteria:**
- [Primary key](#primary-key) is required
- Using row order to convey information is not permitted
- Single cell must not hold more than one value [atomicity](#atomicity)
- Cell values in a column must be of the same data type
- [repeating groups](#repeating-groups) are not permitted
- No duplicated rows or columns

## Second Normal Form (2NF)
**Why we need it:**
- Eliminates [redundancy](#redundancy)
- Removes [partial dependencies](#partial-dependency)

**Criteria:**
- Must be in 1NF
- Each [non-key attribute](#non-prime-attribute) must depend on the *entire* [primary key](#primary-key)

## Third Normal Form (3NF)
**Why we need it:**
- Eliminates [transitive partial dependencies](#transitive-dependency)

**Criteria:**
- Must be in 2NF
- Every [non-key attribute](#non-prime-attribute) in table should depend on "the key, the whole key, and nothing but the key"

## Boyce-Codd Normal Form (BCNF)
**Why we need it:**
- Addresses anomalies not handled by 3NF
- Deals with cases of multiple [candidate keys](#candidate-key)
- Usually, most 3NF tables are also BCNF tables

**Criteria:**
- Must be in 3NF
- every att in a table should depend on the key, the whole key & nothing but the key
*OR*
- For every [functional dependency](#functional-dependency) X → Y, X must be a superkey

## Fourth Normal Form (4NF)
**Why we need it:**
- Addresses [multi-valued dependencies](#multi-valued-dependency)

**Criteria:**
- Must be in BCNF
- The only kinds of multi-valued dependencies allowed in a table are multi-valued dependencies on the key

## Fifth Normal Form (5NF)
**Why we need it:**
- Addresses [join dependencies](#join-dependecy)
- Prevents information loss during decomposition and recomposition

**Criteria:**
- Must be in 4NF
- It must not be possible to describe the table as a join of some other tables having the same key
- Every join dependency in the table is implied by the [candidate keys](#candidate-key)

# Glossary

### <a id="anomalies"></a>Anomalies
When a process fails and results in database state that should not be possible. Types include insertion anomalies, update anomalies, and deletion anomalies.

### <a id="atomicity"></a>Atomicity
The property that requires each cell in a database to contain only a single, indivisible value.

### <a id="candidate-key"></a>Candidate Key
A minimal set of attributes that can uniquely identify a record in a table. "Minimal" means you cannot remove any attribute from the set while maintaining uniqueness.

**Example:** In a university course registration table, either StudentID+CourseID or RegistrationNumber alone could be candidate keys.

### <a id="composite-key"></a>Composite Key
A primary key made of multiple columns combined together.

### <a id="foreign-key"></a>Foreign Key
An attribute or set of attributes in one table that refers to the primary key of another table, establishing a relationship between the tables.

### <a id="functional-dependency"></a>Functional Dependency
When one attribute uniquely determines another attribute. If you know the value of attribute X, you can determine the value of attribute Y. This is written as X → Y (X determines Y).

### <a id="join-dependency"></a>Join Dependency
A condition that occurs when a table can be recreated by joining multiple tables without losing or gaining any information.

### <a id="multi-valued-dependency"></a>Multi-Valued Dependency (MVD)
Each value/key/attribute has a specific set of available values/attributes.

**Example:** A model car can have 3 colors: Blue, Green, Yellow, where "Model car" is the value and "colors" are the set.

### <a id="non-prime-attribute"></a>Non-Prime Attribute
An attribute that is not part of the candidate key.

### <a id="partial-dependency"></a>Partial Dependency
A condition where a non-key attribute depends on only part of a composite primary key, rather than the entire key.

**Example:** PK is: StudentID + CourseID and att is: Student Name. Student name only depends on StudentID and not CourseID. Student name will never change due to CourseID

### <a id="primary-key"></a>Primary Key
A specific column or set of columns that uniquely identifies each row in a table.

### <a id="superkey"></a>Superkey
Any set of attributes that can uniquely identify a record in a table. A candidate key is a minimal superkey.

### <a id="transitive-dependency"></a>Transitive Dependency
A condition where a non-prime attribute is dependent on another non-prime attribute, which in turn depends on the primary key.

**Example:** PK is: StudentID and first non-prime att is Homeroom. Second non-prime att is First Period Teacher. StudentID -> Homeroom -> First Period Teacher 

### <a id="repeating-groups"></a>Repeating Groups
Collections of related data that appear multiple times within a single row of a table. Repeating groups violate first normal form (1NF) and can lead to data access and manipulation problems.

**Example:** A customer table with columns like Customer_ID, Customer_Name, Phone1, Phone2, Phone3 contains repeating groups of phone numbers. This should be redesigned into separate tables to conform to 1NF.

### <a id="redundancy"></a>Redundancy
The unnecessary repetition of data across multiple rows or tables in a database. Redundancy wastes storage space and creates potential inconsistencies during updates, as the same information must be changed in multiple places.

**Example:** If customer addresses are stored in both the Orders table and the Customers table, this creates redundancy. When an address changes, it must be updated in both places or the database will contain inconsistent data.
