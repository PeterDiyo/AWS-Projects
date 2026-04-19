# Serverless Email Marketing Application using AWS

An **event-driven email marketing system** built using AWS services. This project demonstrates how to design a scalable, automated email pipeline using serverless architecture.

## Architecture Overview

- **Event-driven system**
- Fully **serverless and scalable**
- Designed for **automation, reliability, and cost efficiency**

## Architecture Diagram

<img width="319" height="308" alt="Email-market" src="https://github.com/user-attachments/assets/f235074c-8b16-4c69-ae21-dd6bd4bceeb2" />

## AWS Services Used

- **Amazon Simple Email Service (SES)** – Sending emails  
- **Amazon EventBridge** – Scheduling and triggering workflows  
- **Amazon S3** – Storing email templates and contact lists  
- **AWS Lambda** – Processing logic and sending personalized emails  
- **AWS Identity & Access Management (IAM)** – Secure service permissions  


## Requirements

- Basic understanding of AWS services  
- Verified email addresses (recipients) in SES  
- A verified sender email address (must belong to your domain)  

## High-Level Design

- **S3** → Stores HTML email templates and contact lists (CSV)  
- **Lambda** → Fetches templates, merges with contact data, and sends emails  
- **SES** → Handles email delivery  
- **EventBridge** → Triggers email campaigns on a schedule  
- **IAM** → Grants secure access between Lambda, S3, and SES  

## Setup Guide

### 1. Create and Configure S3
- Create an S3 bucket  
- Upload:
  - Email template (HTML file)
  - Contact list (CSV file)
- Check code for both files in this project files

### 2. Configure Amazon SES
- Verify your **sender email address and domain**
- Verify recipient emails (if in SES sandbox mode)
- Ensure SES is out of sandbox (for production use)

### 3. Create the Lambda Function
- Navigate to AWS Lambda → **Create Function**
- Choose **“Author from scratch”**
- Implement logic to:
  - Fetch template from S3  
  - Parse contacts CSV  
  - Inject personalized data (e.g., `{{FirstName}}`)  
  - Send emails via SES  
- Deploy and test the function

### 4. Configure IAM Permissions
- Locate the IAM role created with your Lambda function  
- Attach a policy allowing access to:
  - `s3:GetObject`
  - `ses:SendEmail` / `ses:SendRawEmail`
- Test again to confirm permissions are working

### 5. Schedule with EventBridge
- Create a new **EventBridge Rule / Schedule**
- Define frequency (daily, weekly, monthly, etc.)
- Set target → **Lambda Function**
- Configure input (if needed)
- Create and activate the schedule

### Final Step
- Monitor execution
- Confirm emails are successfully sent via SES
<img width="556" height="520" alt="image" src="https://github.com/user-attachments/assets/70ec8fde-f009-4d0d-b447-1a9cecb8cedc" />

## How to Enhance

### 🔹 1. Replace CSV with DynamoDB
- Store contacts in DynamoDB for:
  - Scalability
  - Faster querying
  - Better segmentation

### 🔹 2. Add a Frontend UI
- Build a dashboard to:
  - Trigger campaigns manually
  - Upload templates
  - Manage contacts  
- Use:
  - **API Gateway
  - React / Next.js (frontend)

## Project Goal

To demonstrate:
- Event-driven architecture  
- Serverless system design  
- Real-world email automation workflows using AWS  
