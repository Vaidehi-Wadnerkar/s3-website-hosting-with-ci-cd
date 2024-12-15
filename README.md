# S3 Website Hosting with AWS CodePipeline Integration

This project demonstrates how to host a static website on Amazon S3 and automate deployments using AWS CodePipeline integrated with GitHub. Below are the detailed steps and insights for setting up the project.

---

## Prerequisites

Ensure you have the following before starting:

1. An AWS account with permissions to create S3 buckets and configure CodePipeline.
2. GitHub account to host your code repository.
3. Basic understanding of AWS S3, GitHub, and CodePipeline.

---

## Steps to Host a Static Website on S3

### 1. Create an S3 Bucket

1. Log in to your AWS Management Console.
2. Navigate to **S3** and click **Create bucket**.
3. Provide a unique bucket name (e.g., `my-website-bucket`).
4. Uncheck the **Block all public access** setting (for this demo, the bucket needs to be public).
5. Click **Create bucket**.

### 2. Upload the `index.html` File

1. Navigate to your bucket in the S3 console.
2. Click **Upload** and add the `index.html` file.
3. After uploading, make the file public:
   - Select the file and go to **Permissions**.
   - Under **Public access**, choose **Make public using ACL**.

### 3. Enable Static Website Hosting

1. Go to your bucket's **Properties** tab.
2. Scroll to the **Static website hosting** section and click **Edit**.
3. Select **Enable**.
4. Provide the following details:
   - **Index document**: `index.html`
   - Leave the **Error document** blank or specify if needed.
5. Save the settings.
6. Copy the **Endpoint URL** provided and test your website in a browser.

---

## Steps to Automate Deployment with AWS CodePipeline

### 1. Push the Code to GitHub

1. Create a new GitHub repository (e.g., `s3-website-hosting-with-ci-cd`).
2. Clone the repository to your local machine:
   ```bash
   git clone https://github.com/<your-username>/my-static-site.git
   ```
3. Add your `index.html` file to the repository:
   ```bash
   cd my-static-site
   cp /path/to/index.html .
   git add index.html
   git commit -m "Initial commit"
   git push origin main
   ```

### 2. Create a CodePipeline in AWS

1. Navigate to **CodePipeline** in the AWS Management Console.
2. Click **Create pipeline** and provide a name (e.g., `MyStaticSitePipeline`).
3. Choose **Source Provider** as **GitHub**:
   - Connect your GitHub account.
   - Select the repository (`my-static-site`) and branch (`main`).
4. For the **Build Stage**, select **Skip build stage** (optional for static websites).
5. For the **Deploy Stage**, choose **Amazon S3**:
   - Select your bucket (`my-website-bucket`).
   - Specify the destination as the root of the bucket.
6. Click **Create pipeline**.

### 3. Verify the Pipeline

1. Test the pipeline by making a change to the `index.html` file:
   ```html
   <h1>Hello, AWS CodePipeline!</h1>
   ```
2. Commit the changes to the `main` branch:
   ```bash
   git add index.html
   git commit -m "Updated index.html"
   git push origin main
   ```
3. Observe the pipeline automatically triggering and deploying the updated file.
4. Refresh the S3 website URL to see the updated content.

---

## Insights & Thoughts

1. **Ease of Deployment**: AWS CodePipeline simplifies the deployment process. By automating the pipeline, you reduce manual steps and ensure faster updates.

2. **Scalability**: This setup is ideal for static websites or prototypes, but additional considerations (like security and access control) are necessary for production use.

3. **Version Control**: Keeping your website code in GitHub ensures proper versioning and collaboration.

4. **Learning Opportunity**: This project introduces you to multiple AWS services and integrates DevOps practices, which are invaluable for future cloud projects.

---

### Feedback

Let me know your thoughts, suggestions, or improvements for this project. Happy coding! 🚀




