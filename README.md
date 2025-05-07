# MERN Stack Blog App Deployment on AWS

## Introduction
This project is a Blog Application built using the **MERN Stack** (MongoDB, Express, React, Node.js), deployed on **AWS** using the **free-tier** services. The backend runs on an EC2 instance, the frontend is hosted via **S3**, and **MongoDB Atlas** is used for database management. Media files are uploaded and stored in another **S3** bucket.

## Project Components
- **MongoDB Atlas**: Cloud database service used to store blog data.
- **AWS EC2**: Used to run the backend (Node.js/Express).
- **AWS S3**: Hosts the frontend and stores media files (images/videos).
- **AWS IAM**: Provides controlled access to S3 for media storage.

## Prerequisites
- MongoDB Atlas account ([Create Account](https://www.mongodb.com/cloud/atlas))
- AWS account ([Create Account](https://aws.amazon.com))
- Tools like `AWS CLI`, `Git`, `Node.js`, and `npm` installed on your local machine.

## Deployment Steps

### 1. MongoDB Atlas Setup
1. Create an account on [MongoDB Atlas](https://www.mongodb.com/cloud/atlas).
2. Set up a **free cluster**.
3. Allow access to your EC2 instance IP in the **Network Access** settings.
4. Create a **database user** and obtain the **MongoDB connection string**.

### 2. Setup S3 for Frontend
1. Create a bucket named `yourname-blogapp-frontend` in the `eu-north-1` region.
2. Disable **Block all public access**.
3. Enable **Static Website Hosting**.
4. Add a bucket policy to allow public access:

   **Bucket Policy:**
   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::yourname-blogapp-frontend/*"
       }
     ]
   }


