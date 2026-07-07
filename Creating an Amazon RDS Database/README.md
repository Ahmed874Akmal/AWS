# 🗄️   Creating an Amazon RDS Database

## 📖 Overview

In this lab, an Amazon RDS MySQL database was created and integrated with an existing web application. The database was configured with secure networking inside a VPC, connected to an EC2 instance, and used as the backend storage for an inventory management application.

The application was then configured using the RDS endpoint and tested by viewing and modifying inventory records stored inside the database.

---

# 🏗️ AWS Services Used

- Amazon RDS
- Amazon EC2
- Amazon VPC
- Security Groups
- MySQL Community Edition

---

# 🎯 Objectives

- Create an Amazon RDS MySQL database
- Configure database networking
- Deploy the database inside a VPC
- Connect an EC2 application to the database
- Configure the application endpoint
- Verify database connectivity
- Test CRUD operations on inventory data

---

# 📝 Lab Steps

## Step 1 — Configure Amazon RDS Database

A new Amazon RDS MySQL database instance was configured.

Configuration included:

- Engine: MySQL Community Edition
- Deployment: Single DB Instance
- Template: Free Tier
- DB Identifier
- Master Username
- Storage
- Connectivity
- Security Group
- Initial Database Name

![Create Database](images/1.png)

---

## Step 2 — Create the Database

The database instance was successfully created.

Database Details:

- Database Identifier: inventory-db
- Engine: MySQL Community
- Status: Available
- Instance Class: db.t3.micro

![Database Created](images/2.png)

---

## Step 3 — Verify Database Connectivity

The Connectivity & Security section was reviewed.

Verified information:

- Endpoint
- Port (3306)
- Database Name
- VPC
- Security Group
- Availability Zone

This information is required for connecting the application.

![Connectivity](images/3.png)

---

## Step 4 — Access the Inventory Application

The Inventory web application was opened.

Initially, the application could not connect to the database because the database settings had not yet been configured.

![Application Before Configuration](images/4.png)

---

## Step 5 — Configure Database Connection

The application settings were updated with the RDS connection information.

Configured values included:

- Database Endpoint
- Database Name
- Username
- Password

After saving the configuration, the application established a successful connection to Amazon RDS.

![Application Settings](images/5.png)

---

## Step 6 — Verify Inventory Data

The Inventory application successfully retrieved records stored inside the Amazon RDS database.

Existing inventory records were displayed correctly, confirming successful communication between the application and the database.

![Inventory Data](images/6.png)

---

## Step 7 — Test Database Updates

Additional inventory records were added through the web application.

The newly inserted records appeared immediately, demonstrating that write operations to the Amazon RDS database were working successfully.

This confirmed full application functionality including database connectivity and data persistence.

![Updated Inventory](images/7.png)

---

# ✅ Results

The lab successfully demonstrated:

- Amazon RDS Deployment
- MySQL Database Configuration
- Secure Networking with VPC
- Security Group Configuration
- EC2 to RDS Communication
- Database Endpoint Configuration
- Web Application Integration
- Inventory Data Retrieval
- Database Write Operations

---

# 🔒 AWS Concepts Demonstrated

- Amazon RDS
- MySQL Community Edition
- Amazon EC2
- VPC Networking
- Security Groups
- Database Connectivity
- Application Configuration
- Relational Databases
- CRUD Operations

---

# 🎓 Conclusion

This lab demonstrated how to deploy an Amazon RDS MySQL database, securely connect it to an EC2-hosted web application, and verify database operations through an inventory management system. Using Amazon RDS eliminates the operational overhead of managing database infrastructure while providing a scalable and reliable managed relational database service.