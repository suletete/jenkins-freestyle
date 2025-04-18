

# **Jenkins Freestyle Project Setup**

## **Understanding Jenkins Jobs**

A **Jenkins Job** is a fundamental unit of work in Jenkins. It represents a task or series of tasks that Jenkins executes automatically, typically as part of a **build**, **test**, or **deployment** pipeline.

Examples of tasks in a Jenkins job:
- Compiling source code
- Running unit/integration tests
- Packaging applications
- Deploying to production or staging environments

Each job can include:
- **Build steps** (e.g., executing shell commands)
- **Post-build actions** (e.g., archiving artifacts, sending notifications)
- **Triggers** (e.g., webhook events from GitHub)

---

## **Creating Your First Freestyle Project**

### Step 1: Create a New Jenkins Job

1. From the Jenkins **Dashboard**, click **“New Item”** from the left menu  
2. Enter a name (e.g., `my-first-job`)  
3. Select **Freestyle Project**  
4. Click **OK**

📸 *(Image placeholder for freestyle job setup UI)*  
![Freestyle Job](https://darey-io-pbl-projects-images.s3.eu-west-2.amazonaws.com/cicd-with-jenkins/jenkins-freestyle.PNG)

---

## **Connecting Jenkins to GitHub (Source Code Management)**

To enable Jenkins to build code from a GitHub repository:

### Step 1: Create a GitHub Repository

- Create a new repository named `jenkins-scm`
- Add a `README.md` file and push it to the **main** branch

### Step 2: Configure GitHub Integration in Jenkins

1. Open the `my-first-job` configuration  
2. Scroll to **Source Code Management**  
3. Select **Git**  
4. Paste your repository URL (e.g., `https://github.com/your-username/jenkins-scm.git`)  
5. Make sure the branch is set to `main`

### Step 3: Save and Build

- Click **Save**
- Trigger the build manually using **Build Now**
- Jenkins will now clone your GitHub repository

✅ You’ve successfully connected Jenkins with GitHub!

---

## **Configuring Build Triggers (Automating Builds)**

Currently, the build only runs when you click **Build Now**.  
To make Jenkins build automatically on code changes, we need to configure **GitHub Webhooks**.

### Step 1: Enable GitHub Webhook Support in Jenkins

1. Go to your job (`my-first-job`)
2. Click **Configure**
3. Scroll to **Build Triggers**
4. Check **"GitHub hook trigger for GITScm polling"**



---

### Step 2: Add Webhook to GitHub

1. Go to your GitHub repository settings
2. Navigate to **Webhooks > Add webhook**
3. Use this URL format:  
   ```
   http://<your-jenkins-public-ip>:8080/github-webhook/
   ```
4. Set the content type to **application/json**
5. Choose **"Just the push event"**
6. Click **Add webhook**

> Ensure that port `8080` is **open** in your cloud server’s **security group** rules.

---

### Step 3: Test the Webhook

Make a change in your GitHub repository, for example:
- Edit the `README.md` file
- Commit and push the change to `main`

📈 You should now see **Jenkins automatically trigger a new build** via the webhook.

---

## ✅ Summary

You have now:

- Created a Jenkins Freestyle project
- Connected it to a GitHub repository
- Configured a GitHub webhook for **automated builds on push**

Up next, we’ll explore creating a **Pipeline Job** and integrating **Docker** for more advanced workflows.

---
