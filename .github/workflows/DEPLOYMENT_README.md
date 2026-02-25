# GitHub Actions Deployment Setup

This repository contains a GitHub Actions workflow (`deploy-dotnet-app.yml`) that automatically builds and deploys the ZavaStorefront .NET application as a container to Azure App Service.

## Prerequisites

Before the workflow can run successfully, you need to configure the following GitHub secrets and variables.

### Required GitHub Secret

| Secret Name | Description |
|---|---|
| `AZURE_CREDENTIALS` | Azure service principal credentials (JSON) for authentication |

**Create the service principal:**

```bash
az ad sp create-for-rbac --name "github-actions-sp" \
  --role contributor \
  --scopes /subscriptions/{subscription-id}/resourceGroups/{resource-group-name} \
  --json-auth
```

Copy the **entire JSON output** and save it as the `AZURE_CREDENTIALS` secret.

**Grant AcrPush role to the service principal:**

```bash
az role assignment create \
  --assignee {service-principal-client-id} \
  --role AcrPush \
  --scope /subscriptions/{subscription-id}/resourceGroups/{resource-group-name}/providers/Microsoft.ContainerRegistry/registries/{acr-name}
```

### Required GitHub Variables

| Variable Name | Description | Example |
|---|---|---|
| `AZURE_CONTAINER_REGISTRY_NAME` | ACR name (without `.azurecr.io`) | `azcrabc123` |
| `AZURE_APP_SERVICE_NAME` | Azure App Service name | `azwbabc123` |

### How to Configure

1. Go to your GitHub repository.
2. Click **Settings** → **Secrets and variables** → **Actions**.
3. Under the **Secrets** tab, click **New repository secret** and add `AZURE_CREDENTIALS`.
4. Under the **Variables** tab, click **New repository variable** and add `AZURE_CONTAINER_REGISTRY_NAME` and `AZURE_APP_SERVICE_NAME`.

### Finding Your Resource Names

```bash
# List resources in your resource group
az resource list --resource-group {your-resource-group-name} --output table
```

Look for:
- **`Microsoft.ContainerRegistry/registries`** → ACR name
- **`Microsoft.Web/sites`** → App Service name
