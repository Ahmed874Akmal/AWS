# AWS IAM User and Group Management

## Overview

This lab demonstrates the implementation of AWS Identity and Access Management (IAM) by creating users, groups, and assigning permissions through IAM policies.

The objective of this lab is to follow AWS security best practices by managing access through IAM Groups instead of assigning permissions directly to individual users.

---

## Architecture Diagram

![Architecture](images/architecture.png)

The IAM structure implemented in this is consists of:

- Three IAM Users:
  - user-1
  - user-2
  - user-3

- Three IAM Groups:
  - EC2-Admin
  - EC2-Support
  - S3-Support

Each group has a specific IAM Policy attached, and users inherit permissions through group membership.

---

## IAM Dashboard

The IAM Dashboard was used to review and manage IAM resources within the AWS account.

### Screenshot

![IAM Dashboard](images/iam-dashboard.png)

### Observations

- 3 IAM User Groups were created.
- 4 IAM Users were available in the account.
- IAM Policies and Roles were visible from the dashboard.
- The dashboard provides a centralized view of identity management resources.

---

## IAM Users Creation

Three IAM users were created to represent different roles within the AWS environment.

### Screenshot

![IAM Users](images/iam-users.png)

### Users

| Username |
|-----------|
| user-1 |
| user-2 |
| user-3 |

### Purpose

The users were created to demonstrate how permissions can be managed efficiently using IAM Groups.

---

## IAM Groups Creation

Three IAM Groups were created to organize permissions based on job responsibilities.

### Screenshot

![IAM Groups](images/iam-groups.png)

### Groups

| Group Name | Description |
|------------|-------------|
| EC2-Admin | Administrative access to EC2 instances |
| EC2-Support | Read-only access to EC2 resources |
| S3-Support | Read-only access to Amazon S3 |

---

## EC2-Admin Group Configuration

### Screenshot

![EC2 Admin](images/ec2-admin.png)

### Assigned User

- user-3

### Permissions

The EC2-Admin group was configured to allow:

- View EC2 resources
- Start EC2 instances
- Stop EC2 instances

### Result

User `user-3` inherits all permissions assigned to the EC2-Admin group.

---

## EC2-Support Group Configuration

### Screenshot

![EC2 Support](images/ec2-support.png)

### Assigned User

- user-2

### Permissions

The EC2-Support group was configured with:

- EC2 Read-Only Access

### Result

User `user-2` can monitor EC2 resources but cannot make modifications.

---

## S3-Support Group Configuration

### Screenshot

![S3 Support](images/s3-support.png)

### Assigned User

- user-1

### Permissions

The S3-Support group was configured with:

- Amazon S3 Read-Only Access

### Result

User `user-1` can view S3 buckets and objects without modification privileges.

---

## User-to-Group Mapping

| User | Assigned Group | Access Level |
|--------|----------------|--------------|
| user-1 | S3-Support | S3 Read-Only |
| user-2 | EC2-Support | EC2 Read-Only |
| user-3 | EC2-Admin | EC2 View, Start, and Stop |

---

## Security Best Practices Applied

This lab follows several AWS security best practices:

- Principle of Least Privilege
- Role-Based Access Control (RBAC)
- Centralized Permission Management
- Separation of Responsibilities
- Group-Based Permission Assignment

---

## Validation Results

| Task | Status |
|--------|---------|
| Create IAM Users | ✅ Completed |
| Create IAM Groups | ✅ Completed |
| Assign Users to Groups | ✅ Completed |
| Configure IAM Policies | ✅ Completed |
| Verify Permission Inheritance | ✅ Completed |

---
---

# Permission Verification

After assigning users to their respective IAM groups and attaching policies, access permissions were tested to verify that the configured policies were working correctly.

---

## S3-Support Access Verification

### Screenshot

![S3 Access Verification](images/s3-access-verification.png)

### Test Performed

User `user-1` logged in and accessed Amazon S3.

### Result

- Successfully viewed available S3 buckets.
- Successfully accessed bucket information.
- No administrative privileges were granted.

### Verification

This confirms that the S3 Read-Only policy was correctly applied through the `S3-Support` group.

---

## EC2-Support Access Verification

### Screenshot

![EC2 Support Verification](images/ec2-support-verification.png)

### Test Performed

User `user-2` attempted to stop an EC2 instance.

### Result

AWS returned an authorization error indicating that the user was not permitted to perform the `ec2:StopInstances` action.

### Verification

This confirms that the EC2-Support group has Read-Only permissions and cannot perform administrative actions on EC2 resources.

### Security Validation

The permission boundary successfully prevented unauthorized modifications to EC2 instances.

---

## EC2-Admin Access Verification

### Screenshot

![EC2 Admin Verification](images/ec2-admin-verification.png)

### Test Performed

User `user-3` attempted to stop the EC2 instance.

### Result

The stop operation was successfully initiated and AWS accepted the request.

### Verification

This confirms that the EC2-Admin group has sufficient permissions to perform administrative EC2 operations including:

- Viewing instances
- Starting instances
- Stopping instances

### Security Validation

Permissions assigned through the EC2-Admin group were successfully inherited by the assigned user.

---

## Access Control Summary

| User | Group | Expected Permission | Verification Result |
|--------|--------|--------------------|--------------------|
| user-1 | S3-Support | S3 Read-Only | ✅ Passed |
| user-2 | EC2-Support | EC2 Read-Only | ✅ Passed |
| user-3 | EC2-Admin | EC2 Start/Stop Access | ✅ Passed |

---

## Conclusion

The IAM implementation was successfully validated through real-world permission testing.

The results demonstrate that:

- Permissions were inherited correctly through IAM Groups.
- Users received only the permissions assigned to their groups.
- Unauthorized actions were blocked.
- Administrative actions were allowed only for authorized users.

This confirms successful implementation of the Principle of Least Privilege and proper IAM access control within the AWS environment.

## Learning Outcomes

By completing this lab, the following concepts were practiced:

- AWS IAM Fundamentals
- IAM Users Management
- IAM Groups Management
- IAM Policies
- Access Control
- Permission Inheritance
- AWS Security Best Practices

---

## Technologies Used

- Amazon Web Services (AWS)
- AWS Identity and Access Management (IAM)

---

## Author

Abdelrahman Mohamed

Faculty of Computers and Information Systems

Artificial Intelligence Department

Egyptian Chinese University (ECU)
