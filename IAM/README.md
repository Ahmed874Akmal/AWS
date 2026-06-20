# 🔐 AWS IAM Lab

## 📖 Overview

This lab introduces AWS Identity and Access Management (IAM) and demonstrates how AWS manages authentication, authorization, and access control through Users, Groups, and Policies.

The lab focuses on understanding how permissions are inherited and how IAM can be used to implement the Principle of Least Privilege.

---

## 🎯 Objectives

This lab demonstrates:

- 👤 Exploring IAM Users
- 👥 Exploring IAM Groups
- 📜 Inspecting IAM Policies
- 🔗 Assigning Users to Groups
- 🔒 Managing Permissions
- 🧪 Testing Access Control
- ☁️ Understanding AWS IAM Architecture

---

## 🏗️ IAM Architecture

The following diagram illustrates the relationship between IAM Users, Groups, and Policies.

![IAM Architecture](./images/IAM.jpeg)

### Permission Flow

```text
User
   ↓
Group
   ↓
Policy
   ↓
AWS Resource
```

Users inherit permissions from the groups they belong to.

---

# 📸 Lab Screenshots

---

## 🏠 IAM Dashboard

The IAM Dashboard provides an overview of IAM resources available in the AWS account.

It displays information about:

- Users
- Groups
- Roles
- Policies
- Identity Providers

![IAM Dashboard](images/00-iam-dashboard.png)

---

## 👤 IAM Users

The AWS account contains four IAM users.

Users represent identities that can authenticate and interact with AWS resources.

In this lab:

- awsstudent
- user-1
- user-2
- user-3

Initially, the lab users do not belong to any groups.

![IAM Users](./images/01-users.png)

---

## 👥 IAM User Groups

Three groups were preconfigured to represent different job roles.

- EC2-Admin
- EC2-Support
- S3-Support

Groups simplify permission management by assigning permissions to multiple users at once.

![IAM Groups](./images/02-user-groups.png)

---

## 📜 EC2 Support Policy

The EC2-Support group uses the AWS Managed Policy:

AmazonEC2ReadOnlyAccess

This policy allows users to:

✅ View EC2 resources

✅ Monitor EC2 instances

❌ Start instances

❌ Stop instances

❌ Terminate instances

This demonstrates Read-Only access.

![EC2 Support Policy](./images/03-ec2-support-policy.png)

---

## 🪣 S3 Support Policy

The S3-Support group uses the AWS Managed Policy:

AmazonS3ReadOnlyAccess

This policy allows users to:

✅ View S3 buckets

✅ List bucket contents

❌ Upload objects

❌ Delete objects

❌ Modify bucket settings

This demonstrates secure storage access with limited permissions.

![S3 Support Policy](./images/04-s3-support-policy.png)

---

## ⚡ EC2 Admin Inline Policy

Unlike the previous groups, EC2-Admin uses a Customer Inline Policy.

Policy:

EC2-Admin-Policy

This policy provides administrative capabilities for EC2 resources.

Users assigned to this group can:

✅ View instances

✅ Start instances

✅ Stop instances

This demonstrates the difference between Managed Policies and Inline Policies.

![EC2 Admin Policy](./images/05-ec2-admin-inline-policy.png)

---

## 🔗 User Assignment - S3 Support

A user was assigned to the S3-Support group.

Permissions are inherited automatically from the group.

This demonstrates Role-Based Access Control (RBAC).

![S3 Assignment](./images/06-user2-added-to-S3-support.png)

---

## 🔗 Final Group Assignment

All users were assigned according to their job responsibilities.

| User | Group |
|--------|--------|
| user-1 | S3-Support |
| user-2 | EC2-Support |
| user-3 | EC2-Admin |

Permissions are inherited automatically through IAM Groups.

![Final Assignment](./images/07-final-group-assignment.png)

---

## 🔗 User Assignment - EC2 Support

The EC2 Support user was successfully added to the EC2-Support group.

This grants the user read-only access to Amazon EC2 resources.

![EC2 Support Assignment](./images/07-user3-added-to-ec2-support.png)

---

## 🔗 User Assignment - EC2 Admin

The EC2 Administrator user was successfully assigned to the EC2-Admin group.

The user now inherits the EC2-Admin Inline Policy.

![EC2 Admin Assignment](./images/08-user3-added-to-ec2-admin.png)

---

# 🔐 Security Concepts Learned

During this lab the following IAM concepts were explored:

- 👤 IAM Users
- 👥 IAM Groups
- 📜 IAM Policies
- 🔗 Permission Inheritance
- 🛡️ Least Privilege Principle
- 🔒 Access Control
- ☁️ AWS Security Best Practices
- 🎭 Role-Based Access Control (RBAC)

---

# 📊 Policy Types Comparison

| Policy Type | Example |
|------------|----------|
| AWS Managed Policy | AmazonEC2ReadOnlyAccess |
| AWS Managed Policy | AmazonS3ReadOnlyAccess |
| Customer Inline Policy | EC2-Admin-Policy |

---

# 🚀 Learning Outcome

After completing this lab, I was able to:

✅ Explore IAM Users and Groups

✅ Understand AWS Managed Policies

✅ Understand Inline Policies

✅ Assign Users to Groups

✅ Implement Permission Inheritance

✅ Apply Role-Based Access Control

✅ Manage AWS Permissions Securely

---

# 👨‍💻 Author

**Abdelrahman Mohamed**

Faculty of Computers and Information Systems

Artificial Intelligence Department

AWS Academy Cloud Architecting
