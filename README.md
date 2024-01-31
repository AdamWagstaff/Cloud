# Cloud Projects

# Demo 1 - Text To Speech Conversion Tool
This demo showcases a step by step guide to create simple static website application using S3, API Gateway, Lambda, DynamoDB, SNS, and Polly on AWS.

The first section documents how to create the site. The second section documents error handling and testing.

## The Architecture
![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/7cf4e115-6174-4f91-ac03-91a7be83cd97)

Before we get into the steps of building this solution. Let's break down each service we will be using. 

### Amazon S3
We will be creating a static website to host this application. As the structure of the website will remain static and the website is small, there is no need to provision more, when we can save money using a static S3 website.

### API Gateway

**Step 1.**

Create an S3 bucket. Using the Amazon S3 console, click Create Bucket. Use a unique name ![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/25a35410-d2c3-43bf-a7d1-44aab08de681) . 

**Step 2.**

Create a DynamoDB table. 

**Step 3.**

Create an SNS Topic.

**Step 4.**

Create an IAM role.

**Step 5.**

Create "New Item" Lambda Function.

**Step 6.**

Create "Text-to-Audio" Lambda Function.

**Step 7.**

Create "Get Item" Lambda Function.

**Step 8.**

Expose Lambda function to RESTful web service.

**Step 9.**

Create User Interface.



