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
 

