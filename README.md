🎯 Objective

To understand serverless computing by creating and deploying a Lambda function that runs code automatically when triggered, without provisioning or managing servers.

This project helps in learning:

Event-driven computing
Resource optimization
Cost-effective deployments
HTTP-trigger-based execution

🧰 Tools and Services Used

AWS Lambda – to create and run the serverless function
Amazon API Gateway – to expose the function through an HTTP endpoint
AWS CloudWatch – to monitor logs and invocations
AWS IAM – for creating an execution role for Lambda
VS Code / AWS Console Editor – for editing and deploying function code
Postman / Browser / Curl – for testing the function endpoint

📂 Repository Contents
File / Folder	Description
index.mjs	Source code for the Lambda function
README.md	Documentation for the project
screenshots/	Contains screenshots of each deployment step
💻 Function Code (index.mjs)
export const handler = async (event) => {
  // TODO implement
  const response = {
    statusCode: 200,
    body: JSON.stringify('Hi evryone,Hello from US!'),
  };
  return response;
};

🚀 Step-by-Step Implementation
1️⃣ Create IAM Role

Go to AWS Console → IAM → Roles → Create Role
Choose Trusted entity type: AWS Service
Use case: Lambda
Attach policy: AWSLambdaBasicExecutionRole
Name it lambda-basic-execution-role → Create role

2️⃣ Create Lambda Function

Open AWS Console → Lambda → Create Function
Select Author from scratch
Function name: myfuntask4
Runtime: Node.js 18.x
Permissions: Select the role lambda-basic-execution-role
Click Create Function

3️⃣ Add Function Code

In the Code source section, paste the above code in index.mjs
Set Handler as index.handler
Click Deploy (Ctrl + Shift + U)

✅ You’ll see a message:

Successfully updated the function code.

4️⃣ Test the Function

Click Test → Configure test event → Create new test event
Event name: testEvent
Click Save → Test

You should see output:

"Hello from Lambda!"

5️⃣ Add an HTTP Trigger (API Gateway)

Go to Configuration → Triggers → Add Trigger
Choose API Gateway
Select:
Create an API
HTTP API
Security: Open
Click Add

You’ll get a URL like:

https://abc123xyz.execute-api.us-east-1.amazonaws.com/default/myfuntask4

6️⃣ Test via Browser or Postman

Open in browser:

https://abc123xyz.execute-api.us-east-1.amazonaws.com/default/myfuntask4

✅ Output:

Hello from Lambda!

Add a query parameter:

https://abc123xyz.execute-api.us-east-1.amazonaws.com/default/myfuntask4?name=Apurva


✅ Output:

"Hi evryone,Hello from US!"

7️⃣ View Logs

Go to Monitor → View Logs in CloudWatch
Check the invocation logs and timestamps.

8️⃣ Clean Up Resources

After testing:
Delete the API Gateway to remove the HTTP endpoint
Delete the Lambda function (myfuntask4)
Delete the IAM role (lambda-basic-execution-role) if not needed
This avoids any unnecessary usage in your free tier.

🧠 Outcome

By completing this project, you will:
Understand Function-as-a-Service (FaaS) concepts
Learn to deploy and test code without managing servers
Use API Gateway triggers with AWS Lambda
Gain hands-on experience with event-driven and serverless architecture
