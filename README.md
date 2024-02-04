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
  
### Data Manipulation - Insert
- Insert is a statement that can be used when you want to add new records to tables.
- As an example, the statement below will enter a new record for 'Beidou' into the 'name' table:
   - The values are passed as parameters much like a function parameter

 ```
  INSERT INTO genshinChars(id, name, vision)
  VALUES(1, 'Beidou', 'Electro'); 
```

- INSERT INTO is the clause that adds the specified row (or rows in this instance as there are 3)
- genshinChars is the table that these entries will be added into
- (id, name, vision) are the parameters that correspond to the columns that the data will be inserted into
- VALUES is the clause that indicates the data being inserted
- (1, 'Beidou', 'Vision') are parameters identifying the values being inserted:
    - 1: Integer added to the id column
    - 'Beidou': string added to the name column
    - 'Electro': string added to the vision column

- A further example using more than one entry:
```
INSERT INTO genshinChars(id, name, vision)
  VALUES(1, 'Beidou', 'Electro');

INSERT INTO genshinChars(id, name, vision)
  VALUES(2, 'Baizhu', 'Dendro');

INSERT INTO genshinChars(id, name, vision)
  VALUES(3, 'Xianyun', 'Anemo'); 

```

### Data Manipulation - Select:
- SELECT statements are used to fetch data from the database.
- SELECT will return all data in a selected column, ie:

```
SELECT vision FROM genshinChars;
```
- This will select the 'vision' columns from the genshinChars table

1. SELECT is the clause that indicates that the statement is a query. This will be used every time that you query data from a database
2. vision specifies the column to query the data from
3. FROM genshinChars specifies the name of the table to query the darta from, in this instance, data is queried from the genshinChars table

- It is also possible to query data from ALL columns in a table using SELECT as below:
```
SELECT * FROM genshinChars;
```

- * denotes "all".
 
### Data Manipulation - Alter
- The ALTER TABLE statement allows you to add a new column to the table.
- ie, the statement below will add a new column named 'region' to the table:

```
ALTER TABLE genshinChars
ADD COLUMN region TEXT;
```

1. ALTER TABLE is the clause that allows you to make the changes to the table
2. genshinChars is the name of the table being changed
3. ADD COLUMN is a clause that allows the addition of a new column to the table
4. TEXT specifies the data type for this new column (Can also be Integer, Date, Real etc)
5. Concerning NULL value: This is used to represent missing or unknown data, if there is no data, it will show as NULL (∅)

### Data Manipulation - Update:
- The UPDATE statement allows edits of the table rows.
- An example of such:

```
UPDATE genshinChars
SET region = 'Liyue'
WHERE id = 1
```

- This will update the record with the id of 1. (It will update the region column in this row to 'Liyue'
- UPDATE is the clause that edits the row in the table
- genshinChars is the name of the table
- SET is the clause that indicates the column to edit (In the above example, it will be the region column).
- WHERE is a clause that indicates which row(s) to update with the new column value. In this instance, it is row with the id of 1.

### Data Manipulation - DELETE
- DELETE FROM statement deletes one or more rows (where specified) from a table.
- The below statement will DELETE ALL records from the genshinChar table where there is no data for the region column:

```
DELETE FROM genshinChars
WHERE region IS NULL
```

- DELETE FROM is the clause that allows deletion of table rows
- genshinChars is the name of the table that we are deleting the data from
- WHERE is the clause that selects the row to delete the information from, in the above instance, we want to delete all of the rows in where region is set to IS NULL
- IS NULL is a SQL condition that will return true is the value is NULL and false otherwise


### Data Manipulation - Constraints
- Constraints are SQL rules that are applied to the values on individual columns.
- They add information on how a column can be used after specifying the data type for each column.
- These can also be used to tell a database to reject inserted data if it does not adhere to a certain restriction set.
  
Some constraints that can be set:
- PRIMARY KEY
    - These are columns that can be used to uniquely identify a row.
    - Any attempt to inert a row with an identical value to a row already within a table will result in a 'constraint violation' which will not allow you to insert a new row.
- UNIQUE
    - These are columns that have a different value for each row. This is very similar to how a primary key works except that the table can have many different UNIQUE columns compared to PRIMARY KEY which can only have one. 
- NOT NULL
    - These columns must have a value and any attempts to insert a row without a value for a NOT NULL column will result in a 'constraint violation' and the row will not be inserted.
- DEFAULT
  - These columns take an additional argument that will be the assumed value for an interted row if no values are specified for that particular column.

- A new table to show an example:
```
CREATE TABLE genshinArchons(
id INTEGER PRIMARY KEY,
archonName TEXT NOT NULL,
region TEXT DEFAULT 'Teyvat'
);
```
- In the above, we have designated the id column as the Primary Key, the archonName to have NOT NULL which means that they cannot be empty and a DEFAULT with the region, meaning if no region is entered, it will default this column to 'Teyvat'.
