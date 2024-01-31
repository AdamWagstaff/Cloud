# Cloud Projects

# Demo 1 - Text To Speech Conversion Tool
This demo showcases a step by step guide to create simple static website application using S3, API Gateway, Lambda, DynamoDB, SNS, and Polly on AWS.


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

**Step 1. Create DynamoDB Table:**
   * Go to DynamoDB console.
   * Create a table named "posts" with a primary key "id" (string).
   * Define columns: id, status, text, url, voice.
![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/ff54bfe7-ff2e-407c-8f90-3f8701d6f6b0)


**Step 2. Create S3 Bucket:**
   * Go to S3 console.
   * Create a new bucket with a globally unique name to store our audio files.
   * Configure bucket settings for public access.
![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/1b1cfdb8-9bb8-4196-b5e4-fbf67fa4fae9)

**Step 3. Create SNS Topic:**
   * Go to SNS console.
   * Create a topic named "newAudioTopic"

**Step 4. Create IAM Role:**
   * Go to IAM console.
   * Create a policy with necessary permissions for Polly, S3, DynamoDB, and SNS.
   * Create a role, assign it to AWS Lambda service, and attach the created policy.
![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/671bc8de-7073-4ac8-82de-f443b545dbfb)


**Step 5. Create "New Item" Lambda Function:**
   * Go to Lambda console.
   * Create a new function named "newTextItem-function" using Python 2.7 runtime.
   * Set environment variables for SNS_TOPIC and DB_TABLE_NAME.
   * Test the function with input data.

**Step 6. Create "Convert Text to Audio" Lambda Function:**
   * Create a new function named "convertToSpeech-function" using Python 2.7.
   * Set environment variables for DB_TABLE_NAME and BUCKET_NAME.
   * Set the SNS trigger using the "newAudioTopic" topic.

**Step 7. Create "Get Item" Lambda Function:**
   * Create a new function named "retrieveItem" using Python 2.7.
   * Set environment variable for DB_TABLE_NAME.

**Step 8. Expose Lambda Functions with API Gateway:**
   * Go to API Gateway console.
   * Create a new API named "myAPI"
   * Create two methods: POST for "New Item" and GET for "Get Item"
   * Enable CORS for cross-origin requests.

**Step 9. Deploy API Gateway:**
   * Deploy the API (e.g., as "dev").
   * Get the API URL for later use.

**Step 10. Create Static Website Interface:**
   * Download the web page package. https://s3.amazonaws.com/aws-bigdata-blog/artifacts/ai-text-to-speech/text-to-speech-demo.zip
   * Modify the script.js file with the API Gateway URL.
   * Create a new S3 bucket for hosting the web page.
   * Upload html, css, and js files to the S3 bucket.

![image](https://github.com/AdamWagstaff/Cloud/assets/137490172/c17cf1b8-40b6-4381-af51-7c0210141893)



