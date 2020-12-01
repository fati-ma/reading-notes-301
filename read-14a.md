# Readings: Database Normalization
## Read:14 a - DB Normalization

### Hello this is ***Fatima*** :smile:, welcome to my blog where I will share with you the notes I take during reading from the resources provided each class. :closed_book: :pencil2:
### You can visit my GitHub repo for the readings notes from [here](https://github.com/fati-ma/reading-notes-301) or GitHub Pages for this webpage markdown file using this [link](https://fati-ma.github.io/reading-notes-301/read-14a ).

### For this class, I will be reading from this resource: `Database Normalization Explained in Simple English` .

### :pushpin: [ Database Normalization Explained in Simple English](https://www.essentialsql.com/get-ready-to-learn-sql-database-normalization-explained-in-simple-english/)


## Article: Database Normalization Explained in Simple English

### Reasons for Database Normalization

The first is to minimize duplicate data. 
The second is to minimize or avoid data modification issues. 
The third is to simplify queries. 


Here, some data which hasn’t been normalized:

![](https://www.essentialsql.com/wp-content/uploads/2014/06/FirstNormalFormUnormalized-1.png)


The first thing to notice is this table serves many purposes including:

1. Identifying the organization’s salespeople
2. Listing the sales offices and phone numbers
3. Associating a salesperson with an sales office
4. Showing each salesperson’s customers

As a DBA this raises a red flag.  In general I like to see tables that have one purpose.  Having the table serve many purposes introduces many of the challenges; namely, data duplication, data update issues, and increased effort to query data.


### Data Duplication and Modification Anomalies

Duplicated information presents two problems:

1. It increases storage and decrease performance.
2. It becomes more difficult to maintain data changes.


### Insert Anomaly

There are facts we cannot record until we know information for the entire row.  In our example we cannot record a new sales office until we also know the sales person.  Why?  Because in order to create the record, we need provide a primary key.  In our case this is the EmployeeID.


### Update Anomaly

In this case we have the same information in several rows. For instance if the office number changes, then there are multiple updates that need to be made.  If we don’t update all rows, then inconsistencies appear.


### Deletion Anomaly

![](https://www.essentialsql.com/wp-content/uploads/2014/06/Intro-Deletion-Anomaly-e1425554658757.png)

Deletion of a row causes removal of more than one set of facts.  For instance, if John Hunt retires, then deleting that row cause us to lose information about the New York office.


### Search and Sort Issues

The last reason we’ll consider is making it easier to search and sort your data.  In the SalesStaff table if you want to search for a specific customer such as Ford, you would have to write a query like:
```
SELECT SalesOffice
FROM SalesStaff
WHERE Customer1 = ‘Ford’ OR
      Customer2 = ‘Ford’ OR
      Customer3 = ‘Ford’
```

The process to redesign the table is database `normalization`.


### Definition of Database Normalization


There are *three common forms of database normalization*: *1st, 2nd, and 3rd** *normal form*. They are also abbreviated as *1NF, 2NF, and 3NF* respectively. 


The forms are progressive, meaning that to qualify for 3rd normal form a table must *first satisfy the rules for 2nd normal form*, and *2nd normal form must adhere to those for 1st normal form*.


The various forms:

- **First Normal Form** – The information is stored in a relational table with each column containing atomic values. There are no repeating groups of columns.
- **Second Normal Form** – The table is in first normal form and all the columns depend on the table’s primary key.
- **Third Normal Form** – the table is in second normal form and all of its columns are not transitively dependent on the primary key
