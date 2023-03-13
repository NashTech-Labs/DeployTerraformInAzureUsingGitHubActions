### Using this template we will be able toset up GitHub Actions to deploy Terraform code in Azure.

## Prerequisites
This is the list of prerequisites required to create a DevOps pipeline:

- **Azure Subscription:** If you don’t have an Azure subscription, create a free account at https://azure.microsoft.com before you start.

- **Azure Service Principal (SPN):** is an identity used to authenticate to Azure.

- **Azure Remote Backend for Terraform:** we will store our Terraform state file in a remote backend location. We will need a Resource Group, Azure Storage Account, and a Container

- **GitHub Account and GitHub Repository:** we need a GitHub Account to create the GitHub Repository and GitHub Actions.


First, we need to authenticate to Azure. To authenticate using Azure CLI, we type:

`az login`

`az account list --output table`

`az account set --subscription <Azure-SubscriptionId>`

`az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/SUBSCRIPTION_ID"`

These values will be mapped to the Terraform variables:

- appId (Azure) → client_id (Terraform).
- password (Azure) → client_secret (Terraform).
- tenant (Azure) → tenant_id (Terraform).

And add these secrets on yout GitHub

- AZURE_CLIENT_ID
- AZURE_CLIENT_SECRET
- AZURE_SUBSCRIPTION_ID
- AZURE_SUBSCRIPTION_SECRET