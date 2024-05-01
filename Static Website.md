This is to create a Static Website hosted by AWS S3

Implementation of the Static Website is easy. Here are the steps taken to perform this task:
  1. Create a bucket on S3, choose a globally unique name, and uncheck the Block All Public Access
  2. Once the bucket has been created, change permissions of the bucket by allowing public access using the JSON-formatted policy
  3. Allow static website hosting on the bucket
  4. Upload the website template and choose index.html for the index

     
Results:
![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/1b60717a-85ef-42c0-bc77-91b971ad8bc3)

Discussion:
Initially, I experience an error whereby no pictures were present when I clicked on the link. Afterwhich, I found out that the images folder has not been uploaded. So I reuploaded it and complete the task
![image](https://github.com/JayPhantom/AWS-Cloud-Portfolio/assets/109772529/4120c039-7146-49e2-96ab-6d5f8d476b81)
