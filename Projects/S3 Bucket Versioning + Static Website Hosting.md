# Goal: Create an S3 bucket, enable versioning, and host a static website. 

**Step 1: Create S3 Bucket **  
  1. Navigate to S3 in the AWS Console. 
  2. Click "Create Bucket" and enter a unique name. 
  3. Disable "Block all public access". 
**Step 2: Enable Versioning**
  1. In bucket Properties, enable Bucket Versioning. 
**Step 3: Upload Website Files**
  1. In bucket Properties, enable Bucket Versioning. 

HTML 
```
<!DOCTYPE html> 
<html> 
<head> 
  <title>My First S3 Website</title> 
</head> 
<body> 
  <h1>Hello from S3</h1> 
</body> 
</html> 
```
  2. Upload this file to your bucket. 
**Step 4: Enable Static Hosting **
  1. In Properties, enable Static Website Hosting and set the index document to index.html. 
**Step 5: Make Files Public **
  1. Under Permissions, add the following Bucket Policy: 

JSON 
```
{ 
 "Version": "2012-10-17", 
 "Statement": [ 
  { 
   "Effect": "Allow", 
   "Principal": "*",
   "Action": "s3:GetObject", 
   "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*" 
  } 
 ] 
}
```
Verification: Access the "Bucket Website Endpoint" in your browser. Confirm the site loads and verify versioning by uploading a new index.html.
