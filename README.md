Project Repository Overview
1. Workflow: deploy-frontend.yml
Location: .github/workflows/deploy-frontend.yml

Purpose: This GitHub Actions workflow automates the deployment of a frontend application to an Amazon S3 bucket and manages the CloudFront distribution.

Overview:

Name: Deploy to S3
Trigger: Runs when changes are pushed to the main branch.
Job Definition: Runs in an ubuntu-latest environment.
Detailed Steps:

Checkout Repository:
Uses actions/checkout@v4 to clone the repository's content, enabling subsequent steps to access the files.
Sync Files to S3:
Runs aws s3 sync to synchronize local project files to the specified S3 bucket, deleting obsolete files and excluding .git files.
Uses GitHub secrets for AWS credentials and the S3 bucket name.
Invalidate CloudFront Cache:
Runs aws cloudfront create-invalidation to clear the CloudFront cache, ensuring updated files are served.
Utilizes the CloudFront distribution ID and AWS credentials stored in GitHub secrets.
Key Benefits:

Facilitates continuous delivery by automating the deployment process whenever a push to main is detected.
2. Images Folder
Purpose: Contains image assets, such as the LMU logo, used for testing and displaying content on the website.

3. JavaScript: visitor-counter.js
Location: js/visitor-counter.js

Purpose: This JavaScript function retrieves and displays the visitor count from an API endpoint.

Function Overview:

Function Name: visitorCounter()
API Endpoint: https://ohsaui5mib.execute-api.us-east-1.amazonaws.com/visitorCounter
How It Works:

fetch():
Initiates a GET request to the API endpoint to retrieve visitor data.
.then(response => response.text()):
Converts the response to text format for processing.
.then((body) => {...}):
Updates the HTML element with id="visitor-counter" to display the visitor count.
4. .gitignore File
Purpose: Specifies files and directories for Git to ignore, preventing them from being tracked or committed.

Breakdown:

Logs:
npm-debug.log*, yarn-debug.log*, yarn-error.log*
Dependency Directories:
node_modules/
Build Directories:
dist/, build/
Environment Variables:
.env
MacOS Specific Files:
.DS_Store
System Files:
Thumbs.db
Purpose:

Security and Privacy: Keeps sensitive data secure by ignoring .env files.
Size Management: Excludes node_modules/ and build directories to keep the repo size manageable.
Clutter Reduction: Prevents system-specific files from cluttering the project.
5. index.html File
Purpose: Main webpage for Eva Geck’s personal portfolio.

Structure Overview:

DOCTYPE Declaration: Declares HTML5.
HTML Elements:
<head>: Contains metadata, links to CSS and JavaScript, and inline CSS.
<body>: Main content including the header, sections, and footer.
Inline Script:

Calls the visitorCounter() function to display the visitor count on page load.
Inline CSS:

Styles for body, headers, contact info, sections, lists, and other elements.
