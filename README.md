# React Application with AWS S3 Deployment

This project demonstrates how to build and deploy a React application to AWS S3 using Jenkins for CI/CD automation.

## Project Structure

* **`main` Branch:** Production-ready branch.
* **`develop` Branch:** Active development branch.
* **Jenkinsfile:** Automated CI/CD pipeline configuration for React application deployment.
* **README.md:** Documentation of the project.

## 1. Prerequisites

* AWS Account with S3 and IAM access.
* Jenkins server installed with necessary plugins (Git, AWS CLI, NodeJS).
* Node.js and npm installed for local development.

## 2. Project Setup

### Clone the Repository

```bash
git clone <your-repository-url>
cd React-Application-with-AWS-S3-Deployment
```

### Switch to the Main Branch

```bash
git checkout main
```

### Install Dependencies

```bash
npm install
```

### Build the React Application

```bash
npm run build
```

### Test the Application Locally

```bash
npm start
```

## 3. AWS S3 Configuration

* Create an S3 bucket (enable static website hosting).
* Set up the bucket permissions to allow public access.
* Note the S3 bucket name for Jenkins deployment.

## 4. Jenkins CI/CD Pipeline

### Jenkinsfile Configuration

* The `Jenkinsfile` is set to automate the following steps:

  * Checkout the source code from GitHub.
  * Install npm dependencies.
  * Build the React application.
  * Sync the build files to the specified AWS S3 bucket.


```groovy

```

## 5. Usage

* Make changes in the `develop` branch.
* Merge changes to the `main` branch for production deployment.

## 6. Troubleshooting

* **Build Errors:** Ensure all Node dependencies are correctly installed.
* **Deployment Errors:** Verify AWS S3 bucket permissions and region configuration.

## 7. Author

* Created by \[SefaliSabnam].

