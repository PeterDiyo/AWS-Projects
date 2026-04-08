# ⚡ TextractFlow

> AI-powered, serverless receipt processing pipeline built on AWS

## 🧩 Problem

Managing and extracting useful data from receipts manually is inefficient, error-prone, and does not scale. Businesses and individuals need an automated way to digitize, organize, and summarize receipts.

---

## 🚀 Overview

**TextractFlow** is a fully serverless, event-driven cloud application that:

- Automatically processes uploaded receipts
- Extracts structured data using AI
- Stores and organizes data in a database
- Sends real-time email summaries

Built using core AWS cloud-native services, this project demonstrates modern **distributed system design**, **event-driven architecture**, and **AI-powered data extraction**.

---

## 🏗️ Tech Stack

- **Storage**: Amazon S3  
- **AI Extraction**: Amazon Textract  
- **Database**: DynamoDB  
- **Compute**: AWS Lambda  
- **Notifications**: Amazon SES  
- **IAM**: Secure service communication  

---

## ⚙️ Architecture Highlights

- Event-driven pipeline (S3 → Lambda)
- Fully serverless (no infrastructure management)
- Scalable & fault-tolerant design
- Loose coupling between services

---

## 🔄 Workflow

1. User uploads a receipt to S3 (`incoming/` folder)
2. S3 triggers a Lambda function
3. Lambda:
   - Calls Textract to extract receipt data
   - Processes and formats structured data
   - Stores results in DynamoDB
   - Sends email summary via SES
4. User receives processed receipt details instantly

---

## 📦 Features

- 🧠 AI-powered receipt parsing (vendor, date, total, items)
- ☁️ Serverless architecture (auto-scaling)
- 📊 Structured data storage (DynamoDB)
- 📧 Automated email notifications
- 🔐 Secure IAM role-based access

---

## 🛠️ Setup Guide

### 1. Create S3 Bucket
- Create bucket
- Add folder: `incoming/`

---

### 2. Create DynamoDB Table
- Table name: `Receipts`
- Partition key: `receipt_id`

---

### 3. Setup Amazon SES
- Verify sender & recipient email addresses

---

### 4. Create IAM Role

**Role Name:** `ReceiptProcessingLambdaRole`

Attach policies:
- AmazonS3ReadOnlyAccess  
- AmazonTextractFullAccess  
- AmazonDynamoDBFullAccess  
- AmazonSESFullAccess  
- AWSLambdaBasicExecutionRole  

---

### 5. Create Lambda Function

- Runtime: Python
- Attach IAM Role above
- Increase timeout: **3 minutes**

#### Environment Variables:

DYNAMODB_TABLE=Receipts
SES_SENDER_EMAIL=your-email@example.com
SES_RECIPIENT_EMAIL=recipient@example.com

---

### 6. Deploy Lambda Code

Paste provided Python code and click **Deploy**

---

### 7. Configure S3 Event Trigger

- Event type: `All object create events`
- Prefix: `incoming/`
- Destination: Lambda function

---

## Testing

1. Upload a receipt to S3 (`incoming/`)
2. Check Lambda logs (CloudWatch)
3. Verify:
   - Data stored in DynamoDB
   - Email received via SES

---

## 🔐 Security Considerations

- IAM roles enforce least privilege access
- No hardcoded credentials
- S3 bucket access controlled
- SES restricted to verified emails

---

## 📈 Scalability

- Lambda auto-scales with incoming events
- DynamoDB handles high throughput
- S3 supports unlimited storage
- Fully event-driven (no bottlenecks)

---

## 👨‍💻 Author

Built as part of a cloud engineering learning journey aligned with MSc Cloud Computing Systems.

---
