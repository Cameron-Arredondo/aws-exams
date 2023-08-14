# Databases and Analytics
Databases allow us to structure the data and efficiently query and search the data.

## Relational Databases
- Similar to excel spreadsheets, these databases have similarities to each other that can be used as links.  Columns can have relationships to other columns in a different table
## NoSQL Databases
These are non relation databases, they have flexible schemas that are good for building modern applications.  In a NoSQL Database you can have data in JSON format. 
Benefits: 
- Flexibility
- Scalability
- High Performance

## Databases & Shared Responsibility Model on AWS
- AWS offers use to manage different databases
- managed databases are easily provisioned, highly available, vertical and horizontally scaling, automated back ups, restoration, operations and upgrades.
- OS patching is handled by AWS
# AWS RDS
Amazon Relation Database Services is a Managed Database Service that uses the SQL query language.  AWS will provide all the features it provides for it's managed Databases.  RDS has storage backed by EBS, you cannot SSH into these databases.
## Hands-On 
In the console you can go to Amazon RDS -> Databases and create a database.  Here is where you will specify whether it should be a production ready DB, dev and or free tier.  You can then customize the EBS type/size, the compute type and networking of the Database.

## ![RDS Solution Architecture](images/RDS-Solution-Architecture.png)
## AWS Aurora
- Aurora is a relational database

Aurora is a proprietary technology from AWS.  Supports both PostgresSQL and MySQL, Aurora is AWS cloud optimized and claims better performance than RDS.  Aurora storage will grow automatically in increments of 10GB.  Not in Free Tier
