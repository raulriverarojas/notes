# Database Paradigms

## Key-Value
**Examples:** Redis, Memcache
- Used primarily for caching
- Simple structure: key for ID, value for data
- Fast lookups and writes

## Wide Column
**Examples:** Cassandra, HBase

**Structure:**
- Similar to Key-Value but more complex
- Rows have keys
- Each row holds one or more column families
- Each column family holds a set of ordered rows

**Characteristics:**
- No strict schema like relational databases
- Can handle unstructured data
- Uses CQL (similar to SQL) but no joins
- Excellent scalability and easy replication across nodes
- Decentralized architecture for horizontal scaling

**Best for:**
- Large volumes of time series data
- **Example use case:** Sensor data, IoT devices
- High-write, low-read workloads

**Not ideal for:**
- Primary application database

## Document (NoSQL)
**Structure:**
- Documents as containers for key-value pairs
- Unstructured documents without schema requirements
- Documents grouped together in collections
- Indexable fields within collections
- Collections organized in logical hierarchies

**Characteristics:**
- Can model relational data to some degree
- No joins
- Encourages data embedding in a single document instead of normalization
- Faster reads, more complex writes and updates
- More general-purpose than Key-Value or Wide Column

**Not ideal for:**
- Disconnected but related data with many writes
  - Example: Social media apps with interconnected friends, posts, comments, likes

## Relational Database
**Origins and principles:**
- Based on relational data modeling theory
- Tried and tested for decades
- Organizes data in its smallest normal form
- Requires predefined schema

**Characteristics:**
- [ACID](#acid) compliant
- Guarantees data validity even during issues, crashes, failures
- Traditionally more difficult to scale
- Some modern relational DBs designed specifically for scalability (e.g., CockroachDB)

**Best for:**
- Most general applications

**Not ideal for:**
- Unstructured data

## Graph DB
**Approach:**
- Treats relationships as data
- Represents data as nodes and relationships as edges

**Advantages:**
- Better performance on larger databases
- Excellent alternative to SQL when database requires many joins

**Best for:**
- Fraud detection
- Knowledge graphs
- Recommendation engines

## Full-text Search DB
**Best for:** Search engines and typeaheads

**Operation:**
- Begin with an index and add data objects to it
- Database analyzes document text and creates searchable data indices
- Similar to an index in a textbook
- User searches scan indices rather than full documents

**Advantages:**
- Fast performance even on large datasets
- Can run various algorithms to:
  - Rank results
  - Filter irrelevant hits
  - Handle typos

**Disadvantages:**
- Can be costly to run at scale

## Multimodal DB
**Examples:**
    - ArangoDB, CosmosDB, OrientDB
**Operation:**
    - Support multiple data models (document, graph, key-value) in a single database system

---

## <a id="acid"></a>ACID
**Definition:** Atomicity, Consistency, Isolation, Durability
