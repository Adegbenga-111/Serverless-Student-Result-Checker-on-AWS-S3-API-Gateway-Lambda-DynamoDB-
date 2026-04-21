# Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-

## 📌 Project Overview
The Student Result Checker is a serverless web application that allows students to retrieve their academic results using a Student ID. The application is fully hosted on AWS using a serverless architecture with no traditional backend server. Students enter their ID on a static website, which queries an API that retrieves result data from a NoSQL database.

## Architecture Overview
### Services Used
|Service | Purpose|
| -------- | -------- |
| Amazon S3| Hosts static frontend website |
| Amazon API Gateway | Handles HTTP API requests|
| AWS Lambda  | Executes backend logic |
| Amazon DynamoDB | Stores student results |
| IAM | Manages permissions securely|

### Diagram 
![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(551)2.png)

Image 01: Architecture Diagram

## ⚙️ How the Application Works
 ### Step 1
User enters Student ID on webpage , as shown in the image below :

![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(588)1.png)
  Image 02: The Frontend webpage 

### Step 2
Frontend JavaScript sends request:
  
   *GET /?student_id=CSC002*

to API Gateway

### Step 3

API Gateway triggers Lambda function

### Step 4
Lambda queries DynamoDB table *student-results*

### Step 5
Result returned as JSON ,as shown below : 

![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(591).png)
  Image 03 : The result in JSON fromat 
  
  ### Step 6
Frontend displays student result, as shown below :

![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(592).png)
  Image 04 : The result displayed on the Frontend website

## 🧱 Project Deployment Steps
### Step 1 — Create DynamoDB Table
Creating DynamoDB Table *student-results* with Partition key  *student_id (String)*

Insert sample record in to the table using openshell, as shown im the image below :

 ![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(561).png)
   Image 05
The command shown in the image were used in the insertion of data into the DB.

### Step 2 — Create Lambda Function
The Image below showns the basic configuration and runtime  of the function
 ![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(565).png)
  Image 06
  
### Step 3 — Assign IAM Permissions to Lambda
 ![Alt SSRC](https://github.com/Adegbenga-111/Serverless-Student-Result-Checker-on-AWS-S3-API-Gateway-Lambda-DynamoDB-/blob/main/Screenshot%20(567).png)
   Image 07
  
### Step 4 — Create API Gateway
Create:
HTTP GET endpoint
Example:

*/?student_id=CSC002*

Enable:
*Lambda Proxy Integration*

Deploy stage:
*firstofthiskind*

### Step 5 — Deploy Static Website on S3
Upload:

index.html

Enable:
*Static Website Hosting*

Set:

*index.html*

Bucket policy:

{

  "Version": "2012-10-17",
  
  "Statement":
  
     [{ "Sid": "PublicReadAccess",
      
      "Effect": "Allow",
      
      "Principal": "*",
      
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::student-result-checker-site/*"
    }]
