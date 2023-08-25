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
