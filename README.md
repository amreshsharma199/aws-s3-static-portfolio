# AWS S3 Static Portfolio - Module 03 (Day 11-15)

## Project Overview
This project demonstrates **Amazon S3 Static Website Hosting** as per Module 03 objectives.

**S3 Configuration:**
- Bucket Name: `amresh-portfolio-2026` (globally unique)
- Region: `ap-south-1` (Mumbai)
- Storage Class: S3 Standard
- Static Website Hosting: Enabled
- Index Document: `index.html`
- Error Document: `error.html`

## S3 Key Concepts Implemented

### 1. Buckets, Objects, Storage Classes
- Bucket = Container for objects
- Object = File + Metadata + Key
- Storage Classes: Standard (website), IA (backup), Glacier (archive)

### 2. Access Control
- ACLs Disabled (Bucket Owner Enforced)
- Block Public Access: Disabled for website hosting
- Bucket Policy: Allow `s3:GetObject` for public read

### 3. Deployment Steps
```bash
# 1. Create Bucket
aws s3 mb s3://amresh-portfolio-2026 --region ap-south-1

# 2. Enable Static Website Hosting
aws s3 website s3://amresh-portfolio-2026/ --index-document index.html --error-document error.html

# 3. Apply Bucket Policy (policy.json)
aws s3api put-bucket-policy --bucket amresh-portfolio-2026 --policy file://policy.json

# 4. Upload Files
aws s3 cp . s3://amresh-portfolio-2026/ --recursive --exclude ".git/*"
```

### 4. Live Endpoint
- S3 Endpoint: `http://amresh-portfolio-2026.s3-website.ap-south-1.amazonaws.com`
- Temporary Live (GitHub Pages): Same build deployed due to AWS verification pending

### 5. Cost & Durability
- Free Tier: 5GB Standard Storage
- Durability: 99.999999999% (11 nines)

## Deliverables
- GitHub Repo: This repo
- Live Website: GitHub Pages link (S3-ready build)
- LinkedIn Post: See PDF

Author: Amresh Sharma | Module 03 - Amazon S3 & Cloud Storage
