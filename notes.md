# Project Implementation Steps

- create folder named frontend:
    + create file named index.html 
    + add the code shown here
- create folder named Backend
    + create folder generate-presigned-url
        - create main.py
    + create folder process-uploaded-file
        - create main.py

## Setting Up Infra

- folder named infra
    + folder named terraform
        - main.tf
        - variables.tf
        - outputs.tf
        - terraform.tfvars

## Bucket Info

- here, we are using 3 buckets
    1. S3 Remote Backend
    2. for uploading files
    3. for frontend hosting (index.html) - for cloud front

## Roles

- in terraform created one role: lambda-exec-role
- attached 2 policies
    + AWSLambdaBasicExecutionRole
    + AmazonS3FullAccess