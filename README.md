# Frontend Repository Documentation

## 1. GitHub Actions Workflow: `deploy-frontend.yml`

### Purpose
Automates the deployment of a frontend application to an Amazon S3 bucket and manages the CloudFront distribution, enabling continuous updates. It deploys to S3 triggered by pushes to the `main` branch.

### How It Works
- **Set-Up**: It uses `actions/checkout@v4` to clone the repository which provides access to project files for subsequent deployment steps.
- **Sync Files to S3**: Synchronizes local files to the S3 bucket, deleting outdated files and excluding hidden `.git` files by using AWS credentials through GitHub secrets.
- **Invalidate CloudFront Cache**: This clears CloudFront cache to serve updated content again thorugh using AWS credentials stored through GitHub Secrets.

### Benefits
Ensures that updates pushed to `main` are automatically deployed and the credentials managed securely using GitHub secrets.

---

## 2. Images Folder

### Purpose
Contains image of the LMU logo, which was used for testing and displaying content on the website.

---

## 3. JavaScript File: `visitor-counter.js`

### Purpose
The `visitorCounter()` function is developed to dynamically fetch and display the visitor count from an external API on the webpage. This function plays a crucial role in ensuring that the frontend displays real-time data, enhancing user interaction by showing how many people have visited the site.

### How It Works
- **Connection**: The `visitorCounter()` function connects to an API endpoint, `https://ohsaui5mib.execute-api.us-east-1.amazonaws.com/visitorCounter`, to get the current number of visitors. This is achieved through a network request made using JavaScript's `fetch()` function.
- **Output**: After receiving the response, the function processes the data, converts it into a format that can be displayed on the webpage, and updates the specific part of the webpage that holds the visitor count.

### Benefits
Integrating the `visitorCounter()` function into the webpage ensures the visitor count displayed is current and updates in real-time. This adds an interactive element to the webpage and helps showcase site traffic, making the user experience more engaging and informative.

---

## 4. `.gitignore` File

### Purpose
Specifies files and directories that should be ignored by Git, preventing them from being tracked or committed.

### How It Works
- Files store logs generated during operations, especially during errors or debugging. Ignoring them helps keep the repository clean and avoids committing unnecessary log data.
- This directory contains all the installed packages required for your project. It's ignored because it can be recreated using `package.json`, making it redundant to include in version control.
- These directories hold the compiled output of your project. Since they can be regenerated during the build process, they are excluded from version control to avoid clutter.

### Benefits
Keeps sensitive information like credentials out of version control, reduces repository size by excluding files that can be regenerated, and avoids clutter from system and build files.

---

## 5. Main HTML File: `index.html`

### Purpose
Serves as the main webpage for the Cloud Resume Challenge. 

### How It Works
- **HTML**: DOCTYPE Declaration defines the document as HTML5.
- **CSS**: Contains metadata, external CSS/JS links, and inline CSS. Provides comprehensive styling for body, headers, lists, and other elements.
- **Content**: File displays main content including the header, sections (Education, Projects, Skills, Experience), and a visitor counter.
- **Inline Script**: Calls `visitorCounter()` to display the visitor count on page load.
- **JavaScript**: Visitor count updated via JavaScript.

---
