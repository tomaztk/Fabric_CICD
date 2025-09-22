# GitHub & Fabric CI/CD sample to operationalize fabric-cicd to work with Microsoft Fabric and GitHub Actions
Contains a GitHub workflow which can be used operationalize [fabric-cicd](https://github.com/microsoft/fabric-cicd) to work with Microsoft Fabric and GitHub Actions. 

This repository demonstrates a Fabric CI/CD scenario using [fabric-cli](https://aka.ms/fabric-cli) and GitHub. It can be easily adapted to other use cases.  

- Fabric items source code is located in the [/src](/src/) folder.  
- Developers should work in isolation within a feature branch.  
- Pull requests to the main branch trigger a best practices analysis pipeline, [bpa.yml](./.github/workflows/bpa.yml), for both semantic models and reports. This process leverages community tools such as [Tabular Editor](https://github.com/TabularEditor/) and [PBI-Inspector](https://github.com/NatVanG/PBI-InspectorV2).  
- Upon a successful merge into the main branch, the deployment pipeline, [deploy.yml](./.github/workflows/deploy.yml), is triggered to ensure automated deployment to the `development` environment.  
- The deployment pipeline, [deploy.yml](./.github/workflows/deploy.yml), also runs daily on a scheduled trigger to deploy to the `production` environment.


## Instructions

- Fork the repo.
- Configure required [Github secrets and variables](#secrets-and-variables) in your repo.
- Run the [deploy](/.github/workflows/deploy.yml) Github workflow to deploy into your tenant.

I added the below GitHub secrets:

- AZURE_CLIENT_ID – My service principal client ID.
- AZURE_CLIENT_SECRET – My service principal secret. Note this is the secret value.
- AZURE_TENANT_ID – My Microsoft Entra tenant ID.

GitHub secrets and variables
Before working on the below example, I first created GitHub secrets and repository variables.
For the benefit of simplicity, I created these in the repository by going to Settings->Secrets and variables->Actions.


## Run scripts locally

Make sure you have the Fabric CLI installed. If not, run:

```bash
$ pip install ms-fabric-cli
```


You can find the workflow in the [/.github/workflows subfolder](/.github/workflows). In the workflow there are comments about what variables are required.

All of the samples of Fabric items provided in the worskpace folder are from the [original fabric-cicd repository](https://github.com/microsoft/fabric-cicd). However, I do recommend testing with your own items stored in a repository that is the backend for a workspace configured with Microsoft Fabric Git integration.

In addition, you can customize the ["parameter.yml" file](/workspace/parameter.yml) to suit your requirements.
