This is a Fortune Teller application that answers Yes, No, or Maybe to your most personal inquries

**Objective:**
  1. Create a Fortune Teller application whereby a question  can be inputted and it will answer either of the three: YES, NO, and MAYBE.
  2. Create Lambda and API Gateway, and connect them together.
  3. Invoke the lambda function using API Gateway.

Below are the steps I took to be able to create the Fortune Teller application:
  1. I created a Lambda function with Python 3.8 runtime environment. I began writing my code on VSCode with the code below.
     ![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/8ce5ffa6-5723-4440-bae9-e86595e916b9)

      After which I have modified the code and inserted into the terminal of Lambda function.
      ![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/5115dfe1-6061-4c95-bc65-be080a3384a7)
    
  2. After deploying and testing in the terminal of Lambda, I created a HTTP API named Fortune API, pointed it to the Fortune Teller Lambda function, and selected the **GET** method
  3. I went to the Fortune API and then configured the Parameter Mapping with the following values (field : value):
     Parameter to modify : querystring.question,
     Modification type : Append,
     Value: $request.querystring.question
     
     Configuring the Parameter Mapping will allow the questions to be inputted since it accepts a string query
    
**Discussion and Results:**
Question: Will it be sunny today?
![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/1a1fe424-071e-4d15-9aa2-7f8f33d76c0f)

Question: Will I be rich?
![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/35ffb552-2cf8-4f10-bec3-99bcfdfb6a0a)

Question: Should I order my food now?
![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/c9e54729-b643-497d-ba46-595ebf3c2d21)

The creation of the Fortune Teller went well. The problem I initially had was where the user input (question) will be configured. I tried including a function to take the user input on the Python code but it did not work. After reasearching, I have determined that the only way was thru the Parameter Mapping on API Gateway where the question from user input will be appended to the Invoke URL.
