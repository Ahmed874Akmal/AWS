#  Monitor an EC2 Instance

## Task 1 – Configure Security Group

The security group was configured to allow HTTP traffic on port 80 from Anywhere IPv4.

![Security Group](images/5.png)

---

## Task 2 – Verify EC2 Instance Configuration

The instance details were reviewed to verify networking and addressing information.

![Instance Details](images/4.png)

---

## Task 3 – Validate Web Server Access

The public IP address was tested using a web browser.

The default Apache web page was displayed successfully.

![Web Server](images/1.png)

---

## Task 4 – Review Instance Diagnostics

Instance diagnostics were checked to verify instance health.

![Diagnostics](images/2.png)

---

## Task 5 – Review System Logs

System logs were inspected to verify successful web server installation.

![System Log](images/3.png)

---

## Task 6 – Review Attached EBS Volume

The attached EBS storage volume was inspected.

![EBS Volume](images/7.png)

---

## Task 7 – Modify Instance Type

The EC2 instance type was changed from t2.micro to t2.small.

![Instance Type](images/6.png)

---

## Task 8 – Start Instance After Modification

The instance was started again after the instance type modification.

![Instance Restart](images/8.png)

---

## Task 9 – Verify Stop Protection

An attempt was made to stop the instance.

AWS prevented the operation because Stop Protection was enabled.

![Stop Protection](images/9.png)

---

## Conclusion

This  demonstrated:

- EC2 instance management
- Security Group configuration
- Web server deployment
- Instance monitoring and diagnostics
- System log analysis
- EBS volume inspection
- Instance type modification
- Stop protection functionality
