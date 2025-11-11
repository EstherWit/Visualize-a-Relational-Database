# Visualize-a-Relational-Database
<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Visualize a Relational Database

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-databases-rds)

**Author:** Esther Moaweni  
**Email:** moaweniesther@gmail.com

---

## Visualise a Relational Database

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_1fddb0b5)

---

## Introducing Today's Project!

### What is Amazon RDS?

Amazon RDS is a managed relational database service in AWS that supports engines like MySQL, making it easy to set up, operate and scale databases. 

### How I used Amazon RDS in this project

In today's project, I used Amazon RDS to create a MySQL database instance in a private subnet, populate it with a newhire table and sample data using MySQL Workbench, and connect it to QuickSight via a secure VPC connection to visualize the data with charts.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how seamlessly QuickSight could connect to my RDS instance through a VPC connection once the security group and private subnet were properly configured.

### This project took me...

This project took me a few hours to complete, as setting up the RDS instance, configuring the private subnet and security group, populating the database with MySQL Workbench, connecting it to QuickSight and creating visualizations required careful configuration and testing.

---

## In the first part of my project...

### Creating a Relational Database

I created my relational database by using Amazon RDS to create a database instance, selecting a MySQL database engine, and configuring settings such as passwords and the free tier to keep costs low while setting up a secure database.

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_43343546)

---

## Understanding Relational Databases

A relational database is a structured system that organizes data into tables with rows and columns, using SQL to manage and query data, to enable efficient data retrieval and storage, such as in AWS RDS for this project.

### MySQL vs SQL

The difference between MySQL and SQL is that SQL (Structured Query Language) is a standardized language used to query and manage data in relational databases, while MySQL is a specific relational database management system (RDBMS) that uses SQL as its query language to store, retrieve and manipulate data.

---

## Populating my RDS instance

The first thing I did was make my RDS instance public because I needed to allow connections from my local machine outside the AWS network, enabling MySQL Workbench to connect to the RDS instance.

I had to update the default security group for my RDS schema because I want MYSQL workbench to access my database. By only allowing  traffic from my current IP address, MySQL Workbench will be able to connect when I use it from my local computer, which makes it good for security.

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_91b9fd1g)

---

## Using MySQL Workbench

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_1fddb0b5)

To populate my database, I used MySQL Workbench to connect to my RDS instance, created a new schema, defined a newhire table with columns for employee data, and executed SQL INSERT statements to add sample records, such as employee details with IDs, names, jobs, and salaries.

---

## Connecting QuickSight and RDS

To connect my RDS instance to QuickSight, I selected Datasets from the QuickSight left-hand panel, clicked New dataset, then Create data source from the top-right corner of the create dataset pop-up. From the database options, I chose RDS, entered the required details like database name, username, password and connection type and then selected Create data source to establish the connection.

This solution is risky because my RDS instance is publicly available. This means anyone can access it, making it vulnerable from hackers and malicious people trying to get my data.

### A better strategy

First, I made a new security group so that I would attach it to quicksight, this way the RDS Security can only accept requests from the QuickSight security group to ensure security.

Next, I connected my new security group to QuickSight by adding the security group ID to the 'Add VPC connection' form in the Manage VPC connections section of QuickSight’s settings, enabling QuickSight to access my RDS instance securely within the VPC.

---

## Now to secure my RDS instance

To make my RDS instance secure I made it not publicly accessible and then created a security group for the RDS and edited the inbound rules to all traffic from the qiucksight security group.

I made sure that my RDS instance could be accessed from QuickSight by attaching the RDS_SecGp security group to the RDS instance and configuring its inbound rules to allow traffic on port 3306 (for MySQL) only from the QuickSight security group, ensuring secure and restricted access within the VPC.

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_1709b26b)

---

## Adding RDS as a data source for QuickSight

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_1709b29b)

This data source is different from my initial data source because it now connects to my RDS instance in a private subnet via a secure VPC connection with QuickSight.

![Image](http://learn.nextwork.org/daring_silver_jolly_badger/uploads/aws-databases-rds_1709b30b)

---

---
