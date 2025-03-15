# Database Indexing in Relational Database Systems

## Introduction to Database Indexing

Database indexing is a data structure technique used to quickly locate and access data in database tables. Without proper indexing, database queries would require scanning entire tables, resulting in poor performance for large datasets.

## How Indexes Work

- Indexes improve database performance by minimizing the number of disk visits required to quickly access data
- Indexes are data structure techniques used to locate and quickly access data
- Several database fields are used to generate indexes
- The main key or candidate key of the table is duplicated into the first column; this becomes the search key

## Index Structure

- Values are kept in sorted order, usually ascending
- The second column is the data reference or pointer
- Pointers contain sets of addresses of disk blocks where that particular key value can be found
- When creating indexes, we create them on specific columns that need to be candidate keys (unique)

## Example Use Case

For tables with numerous lookups on a specific field (like name), create an index with the search key being that field. This assumes the field values are unique.

## How SQL Queries Use Indexes

- Databases store tables in blocks
- Blocks have fixed amounts of space (e.g., 8kb in PostgreSQL)
- Blocks have IDs
- Blocks store all information of a record or "row"
- To query records, blocks need to be loaded into memory and queried
- A full table scan is required without indexes (poor performance for large tables)

## Benefits of Indexing

- When creating an index, we have search keys, blocks, and index blocks
- This allows us to use the search key to get the address of a record directly from the index
- Indexes are stored in databases, typically as binary trees, not as SQL tables
- Indexes are sorted for performance
- Querying over sorted structures is much faster (binary search)
- This is why indexes are usually stored as binary trees

## Performance Considerations

- Indexes make writes slower as inserts on binary trees can be O(n)
- Don't index columns that are frequently changed/updated
- Creating too many indexes can slow down database performance due to overhead

## Best Practices

- Only create indexes on columns that are frequently queried
- Consider the read/write ratio of your application
- Indexing is about balancing query performance against write performance
