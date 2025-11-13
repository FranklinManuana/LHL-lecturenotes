## Visualizing Databases

In this activity, you are going to take a look at the common practice for visualizing relational data: entity relationship diagrams (ERDs).

An ERD can help you understand, explore, and document a database. It can also help you troubleshoot logic or deployment problems, spot inefficiencies, and help improve processes.

ERDs can also be used to design and model new databases, giving engineers or anyone who will need to work with the database an opportunity to identify any logic or design flaws before they're implemented in production.

In general, as a data professional you could use an ERD to:

- Document an existing database structure
- Debug, troubleshoot, and analyze
- Design a new database
- Gather design requirements

Instruction

Watch the video below from Lucid Charts. It provides a great introduction to visualizing a relational database.

### ERDs

To better understand how the tables in a relational database are interconnected, you can use an **ERD**. This kind of diagram displays each table as a box. It links these boxes together indicating what kind of relationship they have with each other, such as one-to-many or one-to-one.

- **Entity**: an entity is an object or concept about which you want to store information. Each table is an entity.
- **Relationships**: this shows how two entities share information in the database.
- **Attributes**: a key attribute is the unique, distinguishing characteristic of the entity. For example, an employee's social security number might be the employee's key attribute.
- **Cardinality**: this specifies the numerical attribute of the relationship between entities. It can be one-to-one, many-to-one, or many-to-many.

Instruction

Watch this video which explores the key principles of how data is modeled using _ERDs_:

https://youtu.be/-fQ-bRllhXc
### Best Practice Tips

Here are some best practice tips for constructing an ERD:

- **Identify the entities:** the first step in making an ERD is to identify all of the entities you will use. An entity is nothing more than a rectangle with a description of the thing that your system stores information about. This could be a customer, a manager, an invoice, a schedule, etc. Draw a rectangle for each entity you can think of on your page. Keep them spaced out a bit.
- **Identify relationships:** look at two entities–are they related? If so, draw a solid line connecting the two entities and add a diamond between them with a brief description of how they are related.
- **Add attributes:** any key attributes of entities should be added using oval-shaped symbols.
- **Complete the diagram:** continue to connect the entities with lines, and add diamonds to describe each relationship until all relationships have been described. Each of your entities may not have any relationships, some may have multiple relationships. That is okay.

## Conclusion

A successful construction project begins with a blueprint. In a similar way, an ERD acts as a blueprint for a data project. A well-organized and structured database can make the projects that leverage that database run a lot more smoothly. Whether you are involved in building a database from scratch or need to extract insights from the data stored in it, the skills to create and read an ERD will provide you with a strong foundation for a successful project.