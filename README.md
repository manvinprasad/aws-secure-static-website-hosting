# **AWS Secure Static Website Hosting with Global Content Delivery, Monitoring & Disaster Recovery**

This project demonstrates how to host a **production-ready static website** on AWS using **Amazon S3 + CloudFront**, protected with **HTTPS, WAF, IAM least privilege**, monitored with **CloudTrail/CloudWatch**, and backed by a **simple Disaster Recovery architecture** using **S3 Cross-Region Replication (CRR)**.
The entire setup is done using the **AWS Management Console**.

---

## 🚀 **Project Purpose**

Host a globally available, secure, monitored, and cost-optimized static website using AWS services, with optional cross-region DR capabilities.
(Reference: Project documentation page 1)

---

## 📌 **Architecture Diagram**

```md!
[AWS Architecture](aws-secure-static-website/AWS_Architecture_Diagram.png)


```

---

# ⭐ **Key Features**

### **🔒 Security**

* HTTPS enforced via **ACM Certificate (us-east-1)**
* **CloudFront Origin Access Control (OAC)** for private S3 access
* **SSE-S3 encryption** for all buckets
* **IAM Least Privilege**
* **AWS Shield Standard & WAF**
* **Block Public Access** enabled on all S3 buckets

---

### **🌍 Global Content Delivery**

* **Amazon CloudFront CDN** for global low-latency access
* Caching → *Managed-CachingOptimized*
* Automatic compression for performance

---

### **💥 Disaster Recovery (DR)**

* **S3 Cross-Region Replication (CRR)**
* DR bucket (us-west-2) for redundancy
* **CloudFront Origin Failover** on HTTP 5xx errors

---

### **📊 Monitoring & Logging**

* **CloudFront Standard Logs** delivered to S3
* **AWS CloudTrail** enabled across all regions
* **AWS Config** for compliance & resource tracking
* **CloudWatch Alarms** + **SNS notifications** for 5xx error rates

---

### **💸 Cost Optimization**

* Free-tier friendly where possible
* CloudFront Standard Logs (free)
* Billing alerts enabled

---

# 🧩 **AWS Services Used**

* Amazon S3
* Amazon CloudFront
* AWS WAF & Shield
* AWS Route 53
* ACM (Certificate Manager)
* AWS IAM
* AWS CloudTrail
* AWS Config
* Amazon SNS
* Amazon CloudWatch

---

# 📂 **Project Structure**

```
.
├── README.md
├── documentation/
│   └── Static Website Hosting with AWS.pdf
├── architecture/
│   └── AWS_Architecture_Diagram.png
```

---

# 🛠️ **Step-by-Step Implementation (Summary)**

### **1. Preparation**

* Select primary & DR regions
* Create IAM user
* Enable billing alerts

### **2. Create S3 Bucket**

* Block public access
* Enable versioning
* Enable SSE-S3

### **3. Request ACM Certificate**

* Request HTTPS certificate in **us-east-1**
* DNS validation through Route 53

### **4. Configure CloudFront**

* Configure OAC
* Enforce HTTPS
* Add DR bucket as secondary origin
* Enable logging

### **5. S3 Bucket Policy**

* Restrict S3 access to CloudFront OAC only

### **6. Route 53**

* Add DNS validation records for ACM
* Create Alias A record → CloudFront

### **7. DR Setup**

* Create secondary S3 bucket
* Configure CRR
* Test replication
* Configure CloudFront Origin Failover

### **8. Monitoring Setup**

* Enable CloudTrail
* Enable AWS Config
* Create SNS alerts
* Create CloudWatch alarms

---

# 🎯 **What I Learned**

* Building secure AWS architectures
* Configuring CloudFront with OAC
* Handling cross-region DR strategies
* DNS, SSL, and global content delivery
* Setting up monitoring & observability
* Implementing least privilege IAM

---

# 📘 **How to Deploy**

1. Create S3 bucket
2. Upload static website files
3. Set up ACM certificate
4. Configure CloudFront
5. Update bucket policy
6. Configure Route 53
7. Enable logging & monitoring
8. (Optional) Set up CRR & failover

---

# 🧹 **Cleanup**

* Disable & delete CloudFront
* Empty & delete S3 buckets
* Remove Route 53 hosted zone
* Delete ACM certificate
* Disable CloudTrail & AWS Config




