# IAM Role Attached to EC2 for S3 Access

## Objective
Allow an EC2 instance to access S3 **without using access keys**, by assigning an IAM Role. This demonstrates secure temporary credentials using AWS Instance Metadata Service.

---

## Steps Performed

### 1. Created an IAM Role
- Service: **EC2**
- Policy attached: **AmazonS3ReadOnlyAccess**
- Role Name: **EC2-S3-ReadOnly**

This role allows EC2 to read S3 objects **without storing any credentials** on the instance.

---

### 2. Launched EC2 Instance
- OS: Amazon Linux / Amazon Linux 2023
- Instance Type: t2.micro / t3.micro (Free Tier)
- Key Pair: practice-key.pem

---

### 3. Attached IAM Role to Running Instance
AWS Console → EC2 → Select instance → **Actions → Security → Modify IAM Role**  
Selected: `EC2-S3-ReadOnly`

This grants the instance permission to access S3 automatically.

---

### 4. Connected to EC2 via SSH

---

### 5. Verified Role Access to S3 (No Access Keys Used)

Checked AWS CLI:

Listed S3 buckets:

If no buckets exist, created one in AWS Console:

Verified again:

**Result:**  
The command ran successfully **without configuring access keys**, proving the IAM Role authentication worked.

---

## Key Understanding

| Feature | Access Keys | IAM Role |
|--------|-------------|----------|
| Credentials stored on server | Yes | No |
| Risk if leaked | High | Very low |
| Rotation | Manual | Automatic |
| Recommended for EC2 | ❌ No | ✅ Yes |

### Why IAM Roles Are More Secure
IAM roles deliver **temporary credentials** to EC2 through the Instance Metadata Service.  
Nothing is stored on the server, so there is **nothing to leak**.  
This is the **standard best practice** in real DevOps environments.

---

## Conclusion
The EC2 instance successfully accessed S3 **using role-based permissions**.  
This hands-on setup demonstrates understanding of:
- IAM Role security
- Instance metadata authentication
- AWS best practices for access management
