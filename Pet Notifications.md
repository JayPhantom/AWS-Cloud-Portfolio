![3 lambda_function](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/3b2431fc-6fc9-41be-86a5-68819b742b7d)**Description:**
This is a notification service whereby a webpage will send a specified message to an email provided by user input. This is project is a demo from Adrian Cantrill's SAA-C03 course.
![9 webpage](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/3e4d66ca-fb13-4a3e-8aa7-4bf4e3be6a55)

**Objective:**
Using State Machine as the crucial component of this project, the following objectives shall be completed:
  1. Host a static website on S3 that will allow users to input the wait time, email address of the receiver, and a personalized message
  2. Connect the S3 bucket to the API Gateway which will consequently invoke an Lambda API function.
  3. A Lambda API function should then process the request and respond with either success or failure status.
  4. If the Lambda API succeeded, the State Machine will be executed which will acknowledge the wait time specified and carry on the message to another Lambda function
  5. Another Lambda function shall be created to process the message to AWS SES
  6. An AWS SES shall be created with verified a email receiver, and email sender that will deliver the message.

**Procedure:**
**Task 1:**
1. Using AWS SES, create two identities. The first identity should indicate where the email is coming from and the second identity shall indicate where the email will be sent.
2. Verify both email notifications by accessing the specified emails and clicking on the link. This will redirect to an AWS website with a Congratulations message as indicated in the picture below
![congrats email notif](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/6d6f590e-02e9-4b46-a0f0-3b474aac8f3f)


**Task 2**
Configure two Lambda functions that can perform two tasks: send emails using SES and an execution role to provide permissions it needs
1. Create an IAM Role for the Lambda function to assume.
2. Create the Lambda function with the newly-created IAM Role as the default execution role
3. Insert the Python code to the lambda_function. When the Lambda function is invoked by the state machine, it will have an event object that contains the destination email address and a brief message.
![3 lambda_function](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/9ae8087c-f936-4c56-9496-b68299cbdba6)

**Task 3**
Configure the State Machine. This manages the flow of the entire application. It will consist of a timer that will pause before a new item is processed (wait item).
1. Create an IAM Role for the State Machine to allow interaction within the AWS services.
2. Create the State Machine thru Step Functions. The provided JSON-file creates the state machine that initially begins with a Timer that waits for a specified time before the Lambda function is invoked and executed, and then completes the entire state machine execution. Below is a picture that indicated the flow of the state machine
   
![4 state machine](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/5d8e3131-5f8e-4f00-8945-9c50a8f49cc8)
4. Continue the configuration of the state machine by selecting the newly-created IAM role in step 1. Additionally, select the ALL option in Logging tab which allows all events in the state machine to be logged in CloudWatch Logs

**Task 4**
Create an API Gateway where the client application commences its processed to the backend
1. Create a Lambda API function. This function provides a response of failure or success after being invoked by the API Gateway. If the process is failed, it provides a 400 response error and when its process is a success, it executes the State Machine
2. Create a Rest API with API Gateway. Create a Resource and enable CORS (Cross Origin Resource Sharing)
3. With the resource selected, create a method with the POST as method type. Additionally, specify the lambda function that was created on the step 1.
4. Deploy the created API Gateway with stage name as prod

**Task 5**
Upload the webpage to host the static website on S3
1. Create an S3 bucket with a globally unique bucket name. Uncheck the _Block all public access._
2. Generate the bucket policy allowing public access to the bucket.
![5bucketpolicy](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/3a7f5a2e-1e8b-4a57-861e-f3176d27f6b4)
4. Enable the static website hosting on S3. Specify the index.html and error.html
5. Once upload is complete, open the link provided on the static website hosting and test the Pet-Cuddle-O-Tron.

**Results and Discussion**
The creation of the messaging system went fairly well. During the test, as I entered the user input on the webpage, it provided an error that the request has failed. I began the investigation with the assumption that the process flow has not entered the State Machine since the Lambda API function is the only component configured to provide an error during a request. Moving forward, I checked the interconnection and configuration details of the services between S3 to API Gateway, and API Gateway to Lambda API function. As it turns out, an incorrect API was set to trigger the Lambda API function. The error was rectified by specifying the API created on Task 4.2 to the Lambda API function.

Following the correction, the webpage provided success response as indicated in the picture below:
![6 webpage](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/f1e8573b-8fdc-4d2d-8b2e-5237e26b6b8a)

With this, the message was sent to the specified email address:
![7 results in email](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/f96009ec-3da8-4387-93ff-c382435a2861)

Cloudwatch Logs recorded the logs for every request:
![8 cw logs](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/89019f17-8231-43ab-90e2-785d2cc22392)

