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

## 3. JavaScript File: `visitor-counter.js`

**Location**: `js/visitor-counter.js`

### Purpose
Fetches and displays the visitor count from an external API.

### Function Overview
- **Function Name**: `visitorCounter()`
- **API Endpoint**: `https://ohsaui5mib.execute-api.us-east-1.amazonaws.com/visitorCounter`

### How It Works
1. **`fetch()`**: Sends an HTTP `GET` request to the API endpoint.
2. **Response Processing**:
   - Converts the response to text format using `.then(response => response.text())`.
3. **DOM Update**:
   - Updates the `innerHTML` of the element with `id="visitor-counter"` to display the count.

### Integration
Ensures real-time visitor counts are shown on the website.

---

## 4. `.gitignore` File

### Purpose
Specifies files and directories that should be ignored by Git, preventing them from being tracked or committed.

### Breakdown
- **Logs**:
  - `npm-debug.log*`, `yarn-debug.log*`, `yarn-error.log*`
- **Dependency Directories**:
  - `node_modules/`
- **Build Directories**:
  - `dist/`, `build/`
- **Environment Variables**:
  - `.env`
- **MacOS Specific Files**:
  - `.DS_Store`
- **System Files**:
  - `Thumbs.db`

### Key Benefits
- **Security**: Keeps sensitive information like credentials out of version control.
- **Efficiency**: Reduces repository size by excluding files that can be regenerated.
- **Cleanliness**: Avoids clutter from system and build files.

---

## 5. Main HTML File: `index.html`

### Purpose
Serves as the main webpage for Eva Geck’s personal portfolio, showcasing her skills, education, and projects.

### Structure Overview
- **DOCTYPE Declaration**: Defines the document as HTML5.
- **`<head>` Section**:
  - Contains metadata, external CSS/JS links, and inline CSS.
- **`<body>` Section**:
  - Displays main content including the header, sections (Education, Projects, Skills, Experience), and a visitor counter.

### Inline Elements
- **Inline Script**:
  - Calls `visitorCounter()` to display the visitor count on page load.
- **Inline CSS**:
  - Provides comprehensive styling for body, headers, lists, and other elements.

### Features
- **Responsive Design**: Ensures the page is viewable on various devices.
- **Dynamic Content**: Visitor count updated via JavaScript.

---
