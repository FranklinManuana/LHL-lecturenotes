## What is a Database?

Generally speaking, a database is a collection of data (information) stored electronically in a structured manner. The way the data is organized determines the type of database.

### Types of Databases

There are four common types of databases:

1. Hierarchical
2. Network
3. Relational
4. NoSQL

#### 1. Hierarchical Databases

Just as in any hierarchy, this database categorizes data in ranks or levels, and the ranks are expressed using links. One perspective is to think about the data as being organized in a parent-child relationship, and the entire database would resemble a tree. Here is an example of a hierarchical database:

|![Diagram showing a hierarchical structure](https://i.imgur.com/23nTU9D.png)|
|---|
|**Image credits - [https://www.geeksforgeeks.org/types-of-databases/](https://www.geeksforgeeks.org/types-of-databases/)**|

##### Components of a Hierarchical Database

- Attributes
- Records
- Links

A hierarchical database consists of a collection of _records_ connected to each other through _links_. Each record is a collection of fields or _attributes_, each of which contains only one data value. A child record can only be linked to only one parent record.

#### 2. Network Databases

Simply put, a network database is a hierarchical database, but with a major tweak. The child records are given the freedom to associate with multiple parent records. As a result, a network or net of database files linked with multiple threads is observed. Here is an example of a network database:

|![Diagram showing a network structure](https://i.imgur.com/MhP6vhP.png)|
|---|
|**Image credits - [https://www.geeksforgeeks.org/types-of-databases/](https://www.geeksforgeeks.org/types-of-databases/)**|

##### Components of a Network Database

- Attributes
- Records
- Links

A network database consists of a collection of _records_ connected to each other through _links_. Each record is a collection of fields or _attributes_, each of which contains only one data value. A child record can be linked to multiple parent records.

#### 3. Relational Databases

Relational databases are the most mature of all databases, and in this database, every record can be linked to every other piece of record.

##### Components of a Relational Database

- Attributes
- Entity
- Relationships
- Cardinality

A relational database is made up of the four components listed above. You will dive deeper into relational databases in the activities to come.

#### 4. NoSQL Databases

A NoSQL, originally referred to as a non-SQL database, is a non-relational database that provides a mechanism for the storage and retrieval of data. A NoSQL database includes simplicity of design, simpler horizontal scaling to clusters of machines, and finer control over availability. The data structures used by NoSQL databases are very different from tables in relational databases which makes some operations faster in NoSQL.

### Database Management Systems

A database management system (DBMS) is essentially nothing more than a computerized data-keeping system. Users of the system are given facilities to perform several kinds of operations on such a system for either manipulation of the data in the database or the management of the database structure itself. DBMSs are categorized according to their database structures or types: hierarchical, network, and relational. You will see reference to RDBMSs which specifically refers to relational DBMSs.

## Conclusion

As a first step in your learning journey, it is important to be aware of the various database types, their components, and corresponding DBMSs. Be sure to take the time now to ground yourself in these basics.