# Structured Query Language (SQL)

- Programming language used to manage and store data in relational databases.
- - Uses simple, declarative statements, allowing for data accuracy, security and integrity

## Relational Databases:
- Relational databases store data in tables made of columns and rows (vs Non-relational such as MongoDB, in where the data is managed in a document style)
- Columns and Rows are what give Relational databases their names due to their "relationship" between tables.
- Software that controls relational databases is referred to a Relational Database Management System (RDBMS) and allows for management and updating through structured query language (SQL)

### Relational Database structure:
- Tables are defined with Key columns that will hold a unique key value for every row (This is called a Primary Key)
- Columns in a table that reference primary keys that belong to other tables are referred to as Foreign keys.
- The data is related through matching values in the key columns to keep them in order
- Rows in each table are also called records. Columns can also be called fields or attributes.

  Example of tables using a primary and foreign key:
  - ModelNo is the primary key column

Product Table:
| ModelNo |  ProductName  | ProductPrice | UnitCost |
|:-----|:--------:| :--------:| ------:|
| 111  | Chair | $160 | $95 |
| 112  |  Table | $120 | $70 |
| 113  | Bookcase | $100 | $55 |
| 114  | Pens | $10 | $4 |

Sales Table:
The primary key (ModelNo) will match up to the keys also in the ModelNo column in the table below, but will be considered a foreign key in a one-to-many relationship
| OrderNo | ModelNo  | ProductPrice | UnitCost |
|:----|:-------:|:--------:|------:| 
| 10-95 | 111  | Chair | $160 | $95 |
| 10-96 | 112  |  Table  | $120 | $70 |
| 10-97 | 113  | Bookcase | $100 | $55 |
| 10-98 | 114  | Pens | $10 | $4 |

The relation here between the product and sales tables is ModelNo as it is the primary key in Products and ForeignKey in Sales (SO able to access the information within the Product table)

## Starter notes (Using SQLite):
- The following will return all of the data from the tableName table (database)
```
SELECT * FROM tableName;
```

- Table: Collection of data organised into rows and columns (These are sometimes referred to as relations).
- Column: A set of data values of a particular type. In the above example, ModelNo, ProductName,ProductPrice etc are the columns.
- Row: Single record in the table, ie, from the above has a ModelNo of 111, a ProductName of Chair etc
