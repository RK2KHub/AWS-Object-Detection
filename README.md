# AWS-Object-Detection
This project explores the integration of Amazon Web Services, an AI-based computer vision service, in  addressing plant disease identification.

# Agrovision - Build and Deploy Python App to Azure Web App

This repository contains a GitHub Actions workflow for building and deploying a Python application to Azure Web App.

## Overview

This project uses GitHub Actions to automate the build and deployment of a Python application to Azure Web App. The workflow is triggered on pushes to the `master` branch and can also be manually triggered.

## Workflow Details

### Trigger

The workflow is triggered on:
- Pushes to the `master` branch
- Manual dispatch

### Jobs

#### Build Job

- **Runs-on:** `ubuntu-latest`
- **Steps:**
  1. **Checkout Code:** Uses `actions/checkout@v4` to check out the repository.
  2. **Set up Python:** Uses `actions/setup-python@v1` to set up Python 3.11.
  3. **Create and Start Virtual Environment:** Creates and activates a virtual environment.
  4. **Install Dependencies:** Installs the required dependencies from `requirements.txt`.
  5. **Zip Artifact:** Zips the application files for deployment.
  6. **Upload Artifact:** Uploads the zipped artifact for use in the deployment job.

####  Job

- **Runs-on:** `ubuntu-latest`
- **Needs:** `build` job

- **Steps:**
  1. **Download Artifact:** Downloads the artifact from the build job.
  2. **Unzip Artifact:** Unzips the artifact for deployment.
  3. **Deploy to Azure Web App:** deploy the application to Azure Web App.

## Usage

To use this workflow, follow these steps:

1. **Set up the repository:**
   - Clone this repository.
   - Ensure you have a `requirements.txt` file with your Python dependencies.

2. **Configure Secrets:**
   - Add your Azure App Service publish profile as a secret named `AZUREAPPSERVICE_PUBLISHPROFILE_C3B9C50494D94BA68EF3930349DA0EB9` in your GitHub repository settings.

3. **Trigger the Workflow:**
   - Push changes to the `master` branch or manually trigger the workflow via the GitHub Actions tab.

## Resources

- [Docs for the Azure Web Apps Deploy action](https://github.com/Azure/webapps-deploy)
- [More GitHub Actions for Azure](https://github.com/Azure/actions)
- [More info on Python, GitHub Actions, and Azure App Service](https://aka.ms/python-webapps-actions)



