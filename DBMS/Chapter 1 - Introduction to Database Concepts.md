# Introduction to Database Concepts
#dbms

## Terminology
- **Database**: A collection of related data.
- **Data**: Known facts that can be recorded and that have implicit meaning.
- **Mini-world / Universe of Discourse**: An aspect of the real world, changes to which are reflected in the database
- **Database management system (DBMS)**: A computerized system that enables users to create and maintain a database. The DBMS is a general-purpose software system that facilitates the processes of defining, constructing, manipulating, and sharing databases among various users and applications

## File storage versus Databases
- In file systems, different types of users may need to access the same data but due to different use cases, **redundant copies of data are made**

### Self describing nature of database
- DBMS contains data along with it’s **meta data** in a catalog
	- Meta data: type, storage format,  description of structure of database
- Data definition is done by users - DBMS does not know about this and uses the catalog to do so
- In file systems, the data definition is done through constructs inside the application
	- Thus the application describes the data, not the data itself

### Data abstraction
- DBMS software will work with any kind of database 
	- the actual implementation and nature of data depends on the meta data
	- this allows dbms to handle different databases *without changing the underlying architecture*
	- data definition is thus not part of the underlying application
	- This is called **program-data independence**
- In a file system, the opposite is true. Thus data definition is highly coupled with the software. 
	- This means a change in every application accessing the same data if any changes to the definition is required
	
- **Program-operation independence**: The user does not know about the implementation of operations of data. They are simply exposed to an abstraction layer for these operations. 
	- Program definition is independent of the implementation of operations

- DBMS gives users a conceptual view of data without implementation details

### Support of multiple views of data
- Different users can view different subsets of data
- This is not possible with a file system

### Sharing of Data and Multiuser Transaction Processing
- DBMS handles **concurrent** transactions on data by **multiple users**
- **Transaction:** *an executing program or process that includes one or more database accesses, such as reading or updating of database records.*
- Transaction properties:
	- **Isolation:**  Each transaction should appear to be occurring in isolation, instead of as a concurrent process
	- **Atomicity:** The entire transaction must be successful or all of it should fail

## Types of Database Users
### Actors on the scene
- Actual users of the database

1. **Database administrators (DBA):**
	- authorizes access to DB, responsible for hardware and software needs for the database
2. **Database designers:**
	- Choose data to be stored and the structure of data
	- Communicate with other users and provide different views of the data
 	- Views are analyzed and integrated with user groups
3. **End Users:**
	- Primary users of database 
	- There are several types of end users:
		1. Casual End Users: 
			- Use queries to occasionally access different views of data
		2. Naive/Parametric Users:
			- Use canned transactions to query and update data
				- Canned transactions are pre programmed transactions
		3. Sophisticated End Users:
			- Engineers, scientists etc., familiar with the database and system that build complex queries and applications
		4. Standalone Users:
			- Use personal database with readymade programs
4. **Software Engineers:**
- Responsible for creating canned transactions, testing, debugging etc.

### Workers behind the scene
1. **DBMS System designers and implementers**
2. **Tool developers** that develop tools for dbms software
3. **Operators and maintenance personnel** 	

## Advantages Of Using a DBMS
1. Control redundancy
	- While multiple views of data is possible, it’s only stored in one place - this is **data normalization**
	- Sometimes data is stored in several places for faster access - **data denormalization / controlled redundancy**
2. Restricts unauthorized access
3. Persistent storage for programming objects - complex data structures from languages like C++ and Java can be serialized and stored
	- Impedance mismatch problem: data structures of programming languages are not compatible with DBMS programming languages structures. Object oriented databases solve this problem
4. Efficient and powerful querying
5. Provides backup and recovery
6. Multiple user interfaces
7. Represent complex relationships between data
8. Enforce integrity constraints
9. Automatic rules and triggers depending on data

### Additional implications:
1. Enforce standards for data 
2. Reduced development time
3. Flexibility in data structure and storage
4. All users have the latest data on update
5. DBMS scales well

### When not to use DBMS:
1. Overhead costs
	- Initial hardware, software, technical expertise investment
	- Overhead for security, concurrency etc.
2. Data is simple and well defined
3. Data is usually static
4. Real time requirements that are tough for DBMS to meet
5. Embedded systems with low storage
6. No need for multiple user access
