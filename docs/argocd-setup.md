# Bootstrapping ArgoCD on GCP: A Comprehensive Guide

## Introduction

Deploying applications on a cloud platform can be a daunting task. In this guide, we will walk you through the process of bootstrapping ArgoCD on Google Cloud Platform (GCP). By the end of this guide, you'll be managing your Kubernetes clusters like a pro!

## Contents

1. Introduction
2. Prerequisites
3. Setting Up a Kubernetes Cluster on GCP
4. Installing ArgoCD on the Cluster
5. Configuring ArgoCD with Google Cloud Source Repositories
6. Deploying an Application with ArgoCD
7. Conclusion

## Prerequisites

Before we begin, ensure you have the following:

### Steps to setup A GCP account with appropriate permissions

Remember to follow the principle of least privilege, only granting the required permissions for the specific tasks at hand, and always aligning with your organization's policies and guidelines.

- **To create a Kubernetes cluster:**
  - Assign the `roles/container.admin` role or create a custom role with `container.clusters.create` and `container.nodes.create` permissions.
- **To get credentials for the cluster:**
  - Assign the `roles/container.developer` role or create a custom role with `container.clusters.get` and `container.clusters.getCredentials` permissions.
- You can assign these roles using the following command:
  ```shell
  gcloud projects add-iam-policy-binding PROJECT_ID --member=MEMBER --role=roles/container.admin
  ```
  Replace `PROJECT_ID` with your project ID and `MEMBER` with the user or service account to which you want to assign the role.

in my case the command becomes

```shell
  gcloud projects add-iam-policy-binding jvillarreal-sandbox --member=user:joseph.villarreal@66degrees.com --role=roles/container.admin
```

### Install The Google Cloud SDK

1. **Open a terminal window.**
2. **Run the following command to download and install the Google Cloud SDK:**
   ```shell
   curl https://sdk.cloud.google.com | bash
   ```
3. **Restart your shell:**
   ```shell
   exec -l $SHELL
   ```
4. **Initialize the SDK:**
   ```shell
   gcloud init
   ```

### Kubernetes CLI (`kubectl`) Installed

1. **First, ensure you have the Google Cloud SDK installed, as `kubectl` can be installed as a part of it.**
2. **Run the following command to install `kubectl`:**
   ```shell
   gcloud components install kubectl
   ```
3. **Verify the installation:**
   ```shell
   kubectl version --client
   ```

### Helm Installed

1. **Download the Helm installation script:**
   ```shell
   curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
   ```
2. **Make the script executable:**

   ```shell
   chmod 700 get_helm.sh
   ```

3. **Run the script to install Helm:**
   ```shell
   ./get_helm.sh
   ```
4. **Verify the installation:**
   ```shell
   helm version
   ```

## Setting Up a Kubernetes Cluster on GCP

```bash
# Create a Kubernetes cluster
gcloud container clusters create my-cluster --region us-central1

# Get the credentials for the cluster
gcloud container clusters get-credentials my-cluster --region us-central1
```

## Installing ArgoCD on the Cluster

```bash
# Add the ArgoCD Helm repository
helm repo add argo https://argoproj.github.io/argo-helm

# Update the repository
helm repo update

# Install ArgoCD
helm install argocd argo/argo-cd
```

## Configuring ArgoCD with Google Cloud Source Repositories

In this section, we'll configure ArgoCD to work with Google Cloud Source Repositories, allowing seamless integration with your existing codebase.

```bash
# Example commands to configure ArgoCD with Google Cloud Source Repositories
# More detailed instructions here
```

## Deploying an Application with ArgoCD

Deploying an application using ArgoCD is a breeze. Here's an example of deploying a sample application:

```bash
# Define the application
# Deploy the application using ArgoCD
```

## Conclusion

Bootstrapping ArgoCD on GCP streamlines the deployment process, providing a powerful way to manage your Kubernetes applications. Follow these steps, and you'll have a scalable and efficient deployment pipeline in no time!
