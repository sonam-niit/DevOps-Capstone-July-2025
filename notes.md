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

**When you implement change bucket name as per your requirement**

1. Create Zip files for Lambda

```bash
cd backend/generate-presigned-url
zip -r lambda.zip .

cd backend/process-uploaded-file
zip -r lambda.zip .
```

2. Create Bucket For Remote Backend

```bash
aws s3api create-bucket \
--bucket devops-accelerator-platform-tf-state-sonam \
--region us-east-1
```

3. DynamoDB Table for Locking

```bash
aws dynamodb create-table \
--table-name devops-accelerator-tf-locker \
--attribute-definitions AttributeName=LockID,AttributeType=S \
--key-schema AttributeName=LockID,KeyType=HASH \
--billing-mode PAY_PER_REQUEST \
--region us-east-1
```

4. Create pipeline for executing Terraform Code

- terraform.yml
