#  - Public & Private Subnets with Bastion Host and NAT Gateway

> A hands-on AWS networking lab demonstrating how to build a secure VPC architecture using public and private subnets, Internet Gateway, NAT Gateway, Route Tables, Security Groups, and a Bastion Host for secure SSH access.

---

## 📖 Overview

This is demonstrates how to build a secure AWS network architecture where:

- A custom VPC is created.
- Public and Private Subnets are configured.
- Internet access is provided through an Internet Gateway.
- Private instances access the Internet using a NAT Gateway.
- A Bastion Host is deployed in the Public Subnet.
- Private EC2 instances are accessible only through the Bastion Host.
- Security Groups and Network ACLs are configured to control traffic.

---

# 🏗️ Architecture

```
                     Internet
                         │
                Internet Gateway
                         │
        ┌─────────────────────────────────┐
        │            Lab VPC              │
        │          10.0.0.0/16            │
        │                                 │
        │   Public Subnet                 │
        │   10.0.0.0/24                   │
        │                                 │
        │  ┌──────────────┐               │
        │  │ Bastion Host │               │
        │  └──────────────┘               │
        │         │                       │
        │         │ SSH                   │
        │         ▼                       │
        │  Private Subnet                 │
        │ 10.0.1.0/24                     │
        │                                 │
        │ ┌──────────────────┐            │
        │ │ Private Instance │            │
        │ └──────────────────┘            │
        │         │                       │
        │         ▼                       │
        │     NAT Gateway                 │
        └─────────────────────────────────┘
```

---

# 🛠️ AWS Services Used

- Amazon VPC
- EC2
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Security Groups
- Network ACLs

---

# 🚀  Steps

---

## Step 1 — Create a Custom VPC

- Name: **Lab VPC**
- CIDR Block: **10.0.0.0/16**

### Screenshot

![Step 1](images/1.png)

---

## Step 2 — Create Public Subnet

Configuration:

- Name: Public Subnet
- CIDR: 10.0.0.0/24
- AZ: us-east-1a

### Screenshot

![Step 2](images/2.png)

---

## Step 3 — Verify Public Subnet

### Screenshot

![Step 3](images/3.png)

---

## Step 4 — Create Internet Gateway

Create an Internet Gateway named:

```
Lab IGW
```

### Screenshot

![Step 4](images/4.png)

---

## Step 5 — Attach Internet Gateway

Attach the Internet Gateway to:

```
Lab VPC
```

### Screenshot

![Step 5](images/5.png)

---

## Step 6 — Configure Public Route Table

Add the route:

| Destination | Target |
|-------------|--------|
| 0.0.0.0/0 | Internet Gateway |

### Screenshot

![Step 6](images/6.png)

---

## Step 7 — Associate Public Subnet

Associate the Public Route Table with the Public Subnet.

### Screenshot

![Step 7](images/7.png)

---

## Step 8 — Launch Bastion Host

Configuration:

- Amazon Linux
- t2.micro
- Public Subnet
- Public IP Enabled

### Screenshot

![Step 8](images/8.png)

---

## Step 9 — Create Bastion Security Group

Inbound

| Protocol | Source |
|----------|--------|
| SSH | My IP |

Outbound

- Allow All

### Screenshot

![Step 9](images/9.png)

---

## Step 10 — Create Private Subnet

Configuration

- Name: Private Subnet
- CIDR: 10.0.1.0/24

### Screenshot

![Step 10](images/10.png)

---

## Step 11 — Create NAT Gateway

Configuration

- Public Subnet
- Elastic IP
- Public Connectivity

### Screenshot

![Step 11](images/11.png)

---

## Step 12 — Verify NAT Gateway

Ensure the NAT Gateway reaches the **Available** state.

### Screenshot

![Step 12](images/12.png)

---

## Step 13 — Configure Private Route Table

Add route

| Destination | Target |
|-------------|--------|
| 0.0.0.0/0 | NAT Gateway |

### Screenshot

![Step 13](images/13.png)

---

## Step 14 — Associate Private Subnet

Associate the Private Route Table with the Private Subnet.

### Screenshot

![Step 14](images/14.png)

---

## Step 15 — Launch Private EC2 Instance

Configuration

- Amazon Linux
- Private Subnet
- No Public IP

### Screenshot

![Step 15](images/15.png)

---

## Step 16 — Create Private Security Group

Inbound Rule

| Protocol | Source |
|----------|--------|
| SSH | Bastion Host Security Group |

Outbound

- Allow All

### Screenshot

![Step 16](images/16.png)

---

## Step 17 — Connect to Bastion Host

Start the SSH agent.

```bash
eval $(ssh-agent -s)

ssh-add lab11.pem

ssh-add vockey2.pem

ssh-add -l
```

### Screenshot

![Step 17](images/17.png)

---

## Step 18 — SSH into Bastion Host

```bash
ssh -A ec2-user@<Public-IP>
```

### Screenshot

![Step 18](images/18.png)

---

## Step 19 — Attempt SSH to Private Instance

```bash
ssh ec2-user@10.0.1.64
```

### Screenshot

![Step 19](images/19.png)

---

## Step 20 — Verify Internet Connectivity

```bash
ping 8.8.8.8
```

### Screenshot

![Step 20](images/20.png)

---

## Step 21 — Configure Network ACL

Inbound Rules

| Rule | Action |
|------|--------|
| 50 | Deny ICMP from 10.0.0.85/32 |
| 100 | Allow All |

### Screenshots

Before

![Step 21](images/21.png)

After

![Step 21](images/22.png)

---

# 🔒 Security Design

- Bastion Host is the only publicly accessible EC2.
- Private EC2 has no Public IP.
- Internet access for Private Subnet is provided through the NAT Gateway.
- SSH access to Private EC2 is restricted to the Bastion Host Security Group.
- Network ACLs demonstrate subnet-level traffic filtering.

---

# ✅ Verification

✔ Custom VPC Created

✔ Public Subnet Created

✔ Private Subnet Created

✔ Internet Gateway Attached

✔ Public Route Table Configured

✔ NAT Gateway Available

✔ Private Route Table Configured

✔ Bastion Host Running

✔ Private EC2 Running

✔ Security Groups Configured

✔ Network ACL Rules Configured

✔ Internet Connectivity Verified

---

# 📂 Project Structure

```
AWS-VPC-Lab/
│
├── README.md
│
└── images/
    ├── 01-vpc-created.png
    ├── 02-public-subnet-create.png
    ├── 03-public-subnet-created.png
    ├── 04-create-igw.png
    ├── 05-attach-igw.png
    ├── 06-route-to-igw.png
    ├── 07-public-association.png
    ├── 08-bastion-launch.png
    ├── 09-bastion-sg.png
    ├── 10-private-subnet.png
    ├── 11-create-nat.png
    ├── 12-nat-created.png
    ├── 13-private-route.png
    ├── 14-private-association.png
    ├── 15-private-instance.png
    ├── 16-private-sg.png
    ├── 17-ssh-agent.png
    ├── 18-bastion-login.png
    ├── 19-private-ssh.png
    ├── 20-ping.png
    ├── 21-nacl-before.png
    └── 22-nacl-after.png
```

---

# 👨‍💻 Author

**Abdelrahman Mohamed**

Faculty of Computers and Information Systems

AWS Academy Labs