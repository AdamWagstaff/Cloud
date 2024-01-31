# Cloud Projects

# Demo 1 - Text To Speech Conversion Tool
This demo showcases a step by step guide to create simple static website application using S3, API Gateway, Lambda, DynamoDB, SNS, and Polly on AWS.

The first section documents how to create the site. The second section documents error handling and testing.

## The Architecture
![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/7cf4e115-6174-4f91-ac03-91a7be83cd97)
**1. Web Interaction**
   * The journey begins as the application sends new post information to our RESTful web service, securely hosted on Amazon API Gateway.
   * Invoking this service is a static webpage residing on Amazon S3, adding a layer of simplicity to the initial interaction.
     
**2. Lambda Kickstart**
   * Amazon API Gateway sets in motion the dedicated Lambda function, "New Item," marking the inception of the MP3 file generation process.
   * This Lambda function efficiently inserts post details into our DynamoDB table, meticulously storing information for all posts.
     
**3. Decoupling with SNS**
   * To ensure asynchronous processing, Amazon SNS steps in, decoupling the reception of new post information and the initiation of the conversion process.
   * "Convert Text To Audio", another Lambda function, eagerly subscribes to the SNS topic, awaiting the trigger for post-to-audio conversion.
     
**4. Polly's Artistry**
   * Triggered by the appearance of a new message on the subscribed SNS topic, the "Convert Text To Audio" Lambda function employs Amazon Polly's prowess, transforming text into an audio file.
   * The audio masterpiece finds its home in a designated S3 bucket, eagerly awaiting retrieval.
     
**5. Post-Processing**
   * DynamoDB tables undergo updates as the newly created MP3 file's reference (URL) to the S3 bucket is harmoniously linked with existing item data.

**6. Gateway for Information**
   * When the application seeks item information, the RESTful web service, confidently deployed through Amazon API Gateway, exposes methods catering to information retrieval.
   * A static webpage on Amazon S3 seamlessly interacts with this service, initiating the process.
     
**7. Lambda Logic Unleashed
   * Amazon API Gateway seamlessly triggers the "Get Item" Lambda function, the gateway to retrieving item data.
   * This Lambda function, with finesse, fetches detailed item information, including the pivotal link to the Amazon S3 bucket.
     
**8. DynamoDB Dexterity**
   * Empowered by DynamoDB, the "Get Item" Lambda function navigates through the stored data, assembling a comprehensive snapshot of the item, including the reference to the S3 bucket.


## Guide

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



