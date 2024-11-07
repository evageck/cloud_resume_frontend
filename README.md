# Project Repository Documentation

## 1. GitHub Actions Workflow: `deploy-frontend.yml`

**Location**: `.github/workflows/deploy-frontend.yml`

### Purpose
Automates the deployment of a frontend application to an Amazon S3 bucket and manages the CloudFront distribution, enabling continuous delivery.

### Overview
- **Name**: Deploy to S3
- **Trigger**: Triggered by pushes to the `main` branch.
- **Environment**: Runs on `ubuntu-latest`.

### Detailed Steps
#### 1. Checkout Repository
- **Action**: Uses `actions/checkout@v4` to clone the repository.
- **Purpose**: Provides access to project files for subsequent deployment steps.

#### 2. Sync Files to S3
- **Command**: `aws s3 sync . s3://${{ secrets.S3_BUCKET_NAME }} --delete --exclude ".git*"`
- **Description**: Synchronizes local files to the S3 bucket, deleting outdated files and excluding hidden `.git` files.
- **Credentials**: Uses `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, and `S3_BUCKET_NAME` stored as GitHub secrets.

#### 3. Invalidate CloudFront Cache
- **Command**: `aws cloudfront create-invalidation --distribution-id ${{ secrets.CLOUDFRONT_DISTRIBUTION_ID }} --paths "/*"`
- **Purpose**: Clears CloudFront cache to serve updated content.
- **Credentials**: Utilizes `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`, and `CLOUDFRONT_DISTRIBUTION_ID` stored as GitHub secrets.

### Benefits
- **Continuous Deployment**: Ensures that updates pushed to `main` are automatically deployed.
- **Security**: Credentials managed securely using GitHub secrets.

---

## 2. Images Folder

### Purpose
Contains image assets, such as the LMU logo, which is used for testing and displaying content on the website.

---

## 3. JavaScript File: `visitor-cou
