This is to create a Static Website hosted by AWS S3

**Objectives:**
  1. Create a static website hosted on S3

Implementation of the Static Website is easy. Here are the steps taken to perform this task:
  1. Create a bucket on S3, choose a globally unique name, and uncheck the Block All Public Access
  2. Once the bucket has been created, change permissions of the bucket by allowing public access using the JSON-formatted policy
  3. Allow static website hosting on the bucket
  4. Upload the website template and choose index.html for the index. The website template was obtained from a free-css.com

     
**Results:**

![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/1b60717a-85ef-42c0-bc77-91b971ad8bc3)


**Discussion:**
When I clicked on the client after the creation, no error was present. Afterwhich, I found out that the images folder of the website files has not been uploaded. So I reuploaded it and completed the task

![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/4120c039-7146-49e2-96ab-6d5f8d476b81)


The JSON-formatted bucket policy allows public access to all the objects contained inside **carvillaexamplejpc** bucket 

![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/487aa54c-9640-41b9-a1be-d65135a0746e)

**Recommendations:**
Use Route 53 for domain name registration
