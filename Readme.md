# Hosting a Static Website Using an AWS S3 Bucket

### Introduction

Amazon S3 (Simple Storage Service) is a highly scalable, reliable, and cost-effective object storage solution from Amazon Web Services. It's a fantastic option for hosting static websites that consist of HTML, CSS, JavaScript, and image files. In this article, we'll guide you through the entire process.

### Prerequisits

* An AWS account (If you don't have one, you can sign up at https://aws.amazon.com)
* A basic understanding of HTML, CSS, and potentially JavaScript if your website uses it.

## Steps
### 1. Create an S3 Bucket

* Log into your AWS Management Console and navigate to the S3 service.
* Click "Create bucket."
* Give your bucket a unique name (ideally matching your domain name if you will be using one).
* Choose the AWS Region that's geographically closest to your target audience.
* Leave the other settings at their defaults for now, and click "Create bucket."

### 2. Enable Static Website Hosting

* Select your newly created bucket.
* Go to the "Properties" tab.
* Click on "Static website hosting."
* Select "Use this bucket to host a website."
* In the "Index document" field, enter "index.html."
* Click "Save changes."

### 3. Adjust Bucket Permissions


* In the "Permissions" tab, you'll need to make your bucket publicly accessible. Click "Edit" next to "Block public access."
* Uncheck all the "Block all public access" settings and save your changes.
### 4. Create a Bucket Policy

* Click on the "Bucket Policy" section under the "Permissions" tab.
* Use the following policy, replacing your-bucket-name with your actual bucket name:

JSON
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::your-bucket-name/*"
        }
    ]
}
```
* Click "Save changes" to apply the policy.

### 5. Upload Website Files


* Go back to the "Overview" tab of your S3 bucket.
* Click "Upload" and either drag and drop your website files (index.html, CSS, JavaScript, images) or select them from your computer.
* Click "Upload."

### 6. Access Your Website

* Find the "Endpoint" URL for your hosted website in the "Static website hosting" section of the "Properties" tab. It will look like http://your-bucket-name.s3-website.your-aws-region.amazonaws.com.
* Open the endpoint URL in your web browser to view your website!

