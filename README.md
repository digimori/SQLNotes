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

# Queries
- Using SQL commands to query a database (Retrieve data from a database)

As an example, we can use the following dataset to show query examples:
Table: relics

|ID| relicName | twoPiece | fourPiece | area |
|-----|-----|------|-----|-----|
|1| Watchmaker, Master of Dream Machinations | Increases Break Effect by 16%. | When the wearer uses their Ultimate on an ally, all allies' Break Effect increases by 30% for 2 turn(s). This effect cannot be stacked. | Path of Dream Dive |
|2| Pioneer Diver of Dead Waters | Increases DMG dealt to enemies with debuff by 12%. | Increases CRIT Rate by 4%. The wearer deals 8%/12% increased CRIT DMG to enemies with at least 2/3 debuffs. After the wearer inflicts a debuff on enemy targets, the aforementioned effects increase by 100%, lasting for 1 turn(s). | Path of Dream Dive |
|3| Passerby of Wandering Cloud | Increases Outgoing Healing by 10%. | At the beginning of the battle, immediately regenerates 1 Skill Point. | Path of Drifting |
|4| Prisoner in Deep Confinement | ATK increases by 12% | For every DoT the target enemy is afflicted with, the wearer will ignore 6% of its DEF when dealing DMG to it. This effect is valid for a max of 3 DoTs. | Path of Darkness |

```
SELECT * FROM relics
```
- The above is selecting all entries/records from the "relics" table.
- SELECT is used whenever you want to start a query with the database
- * is a wildcard meaning "All"
- FROM is stating where you want to query this information from, in which this instance is the "relics" table
  
In the instance, for example, that we are only interested in two columns (columns 1 and 2. ID and relicName), we can break down the query like so:
```
SELECT column1, column2
FROM table_name;

or, as with the above table:
SELECT ID, relicName
FROM relics;
```

## Queries: 'AS'
- 'AS' is a keyword that allows a column or table to be renamed using an alias. This alias is not a change to the column, but merely gives it an alternate name to display (To look a bit more clean).
- Using the above example, we can change 'area' to 'CavernOfCorrosion'
```
SELECT area AS 'CavernOfCorrosion'
FROM relics;
```
- Bear in mind that the use of quotation marks can vary with different Databases. The above works in SQLite, but may vary between either no or double quotes for PostgreSQL.

## Queries: 'DISTINCT'
- 'DISTINCT' is used to return unique values in its output. It filters out all duplicate values in the columns specified in the query.
Example:
```
SELECT tools FROM inventory;
```
- This may produce values such as:
    - hammer, nails, nails, nails, wrench
  - It will not put nails as a single entity despite there being multiple. And given distinct is often used to find out what different (distinct) values exist in a column, this method can become unruly when there are multiples of each item.
  - To fix this, we use DISTINCT:

```
SELECT DISTINCT tools FROM inventory;
```

- This will now produce, going on the example previous: hammer, nails, wrench, as it has chosen only the distinct value of nails and not every entry containing it as it was doing before.


## Queries: WHERE
- The WHERE clause allows us to restrict queries in order to oinly obtain the select information that we want from the table
- ie:
```
SELECT * FROM music WHERE song_rating > 5;
```
- This above example will filter the music table to only display the information from the column in where the song_rating is greater than 5.
- You can use other operators for this, ie: =, !=, <, >, >=, <= as you would in languages such as JavaScript (Like JS, there are special operators also).

## Queries: LIKE I
- Can be used to compare similar values.
- As an example below, for a movie table, there may be two movies with similar titles such as 'Seven' and 'Se7en'.
- You can use Like to select all movies that start with both "se" and end with "en" and have exactly one character in the middle so that we don't bring up every movie ever with those parameters.
- This is where we use LIKE to evaluate the selected column for a sepcific pattern, ie: 'Se_en'. The _ allows substitution of any individual character without breaking up the pattern.

```
SELECT * FROM movies WHERE name LIKE 'Se_en';
```

Queries: LIKE II
- Another comparison, but with the use of a different pattern wildcard: %
- It is NOT Case sensitive
- So by using it, we can filter a table to select only the results that begin with the letter A:
```
SELECT * FROM movies WHERE name LIKE 'A%';
```
- This is also the case in reverse, so to search for anything ending in 'a': %a
- It can also be used as a before and after pattern:

```
SELECT * FROM movies WHERE name LIKE '%man%';
```
- This will bring up every result where the letters 'man' appear. This can be anything from 'Spiderman' to 'The Human Centipede'.
- Bear in mind, you may also need to apply spaces. So if you are looking for something that comes after "The", you will need to add a space before %.
