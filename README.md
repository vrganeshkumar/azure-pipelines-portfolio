# Azure DevOps Pipeline Templates

Production-style CI/CD pipeline templates built and maintained by V R Ganesh Kumar — Azure DevOps Engineer.

These are reference implementations I use when setting up CI/CD for client projects: clean stage separation, environment approvals, and IaC-driven deployments rather than manual click-ops in the Azure portal.

## What's inside

| Pipeline | What it does |
|---|---|
| `pipelines/ci-cd-dotnet-webapp.yml` | Build, test, and deploy a .NET app to Azure App Service across Dev → Staging → Prod, with manual approval gates before Prod |
| `pipelines/iac-deploy-bicep.yml` | Validates and deploys Bicep templates with what-if preview before actual deployment |
| `pipelines/docker-build-push-acr.yml` | Builds a container image, scans it, and pushes to Azure Container Registry with semantic-version tagging |

## Why these patterns

- **Stage gates, not branch luck.** Every environment promotion requires an explicit approval step — nothing reaches Prod just because a merge happened.
- **Infra as code, not portal clicks.** Deployments use Bicep + `what-if` so changes are reviewed before they're applied.
- **Secrets stay in Key Vault**, referenced via variable groups — never hardcoded in YAML.

## Using these templates

1. Copy the relevant YAML into `.azure-pipelines/` in your repo
2. Update the `variables` block with your subscription, resource group, and app names
3. Create a Variable Group in Azure DevOps linked to your Key Vault
4. Set up environments (`dev`, `staging`, `prod`) with the approval checks you need

---

**Need a pipeline like this set up for your team?** I do Azure DevOps + Bicep implementation work — reach out at vrganesh936@gmail.com.
