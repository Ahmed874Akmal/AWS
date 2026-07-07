# 🔐  - IAM Users, Groups and Permissions

## 📖 Overview

This lab demonstrates Identity and Access Management (IAM) in AWS by creating users, groups, assigning permissions, and validating access control through permission testing.

---

# 🏗️ AWS Services Used

- AWS IAM
- IAM Users
- IAM Groups
- IAM Policies
- EC2

---

# 🎯 Objectives

- Create IAM Users
- Create IAM Groups
- Assign AWS Managed Policies
- Add Users to Groups
- Test Access Permissions
- Validate Principle of Least Privilege

---

# 📝  Steps

## Step 1 — Create IAM Groups

Three IAM groups were created:

- EC2-Admin
- EC2-Support
- S3-Support

Each group was configured with different permission levels.

![IAM Groups](images/3.png)

---

## Step 2 — Create IAM Users

Three IAM users were created:

- user-1
- user-2
- user-3

Console access was enabled for all users.

![IAM Users](images/1.png)

---

## Step 3 — Verify User Security Credentials

User security settings, console access, passwords, and access key options were verified.

![User Credentials](images/2.png)

---

## Step 4 — Review IAM Policy

The AmazonEC2ReadOnlyAccess managed policy was reviewed to understand the permissions granted.

Key permissions included:

- EC2 Describe actions
- Load Balancer Describe actions
- CloudWatch monitoring access
- Auto Scaling visibility

![Policy Details](images/4.png)

---

## Step 5 — Add User to IAM Group

User-1 was successfully added to the S3-Support group.

![User Added To Group](images/5.png)

---

## Step 6 — Test Restricted Access

User-2 attempted to stop an EC2 instance.

AWS denied the action because the assigned permissions did not allow the `ec2:StopInstances` operation.

This confirms correct permission enforcement.

![Access Denied](images/6.png)

---

## Step 7 — Verify Authorized Access

User-3 successfully stopped the EC2 instance.

This demonstrates that the assigned permissions were sufficient for performing the requested action.

![Successful Action](images/7.png)

---

# ✅ Results

The lab successfully demonstrated:

- IAM User Creation
- IAM Group Management
- Policy Assignment
- Access Control
- Permission Validation
- Least Privilege Security Model

---

# 🔒 Security Concepts Demonstrated

- Authentication
- Authorization
- IAM Policies
- Role-Based Access Control (RBAC)
- Principle of Least Privilege

---

# 🎓 Conclusion

AWS IAM provides fine-grained access control for AWS resources. By using users, groups, and policies, organizations can enforce security best practices while ensuring that users have only the permissions necessary to perform their tasks.
