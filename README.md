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

### Data Types:
- All data stored in a relational database is of some data type or another. For example:
 - INTEGER - A positive or negative whole number
 - TEXT - A string
 - DATE - Dates (Formatted in: YYYY-MM-DD)
 - REAL - Decimal values (Float numbers)

## Data Manipulation - Statements:
- A statement is a syntax that the database will recognise as a valid command and will always end in a semi-colon (;).

  Example:
```
CREATE TABLE tableName (
column1 dataType,
column2 dataType,
column3, dataType
);
```

A breakdown of the components used in the above example:
1. CREATE TABLE - This is a clause (Clauses are commands which perform specific tasks in SQL and by convention, always use capital letters)
   - Example of Clauses is the SELECT and FROM in a SELECT * FROM tableName statement.   
2. tableName - This is referring to the name of the table (Like the above example with Products and Sales)
3. The data contained in the body of the statement () is a parameter which contains a list of columns and the datatypes being used within them (or, associated data type)
   - Statements can be written as one line or multiple, this can vary depending on the size and readability required.
  
   
