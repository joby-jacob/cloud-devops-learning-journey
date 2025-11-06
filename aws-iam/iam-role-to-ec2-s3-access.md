# IAM Role Attached to EC2 for S3 Access

## Objective
Allow an EC2 instance to access S3 without using access keys. This demonstrates secure, temporary credentials through IAM roles.

## Steps Performed

### 1. Created an IAM Role
- Service: EC2
- Attached Policy: `AmazonS3ReadOnlyAccess`
- Role Name: `EC2-S3-ReadOnly`

### 2. Launched EC2 Instance
- AMI: Amazon Linux
- Instance Type: t3.micro
- Key Pair: practice-key.pem

### 3. Attached IAM Role to Running Instance
EC2 Console → Select Instance → Actions → Security → **Modify IAM Role**  
Selected: `EC2-S3-ReadOnly`

### 4. Connected to EC2 via SSH
