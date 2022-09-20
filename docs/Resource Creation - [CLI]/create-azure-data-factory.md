# Create new Azure Data Factory

### Table Of Contents
- [Pre-Requisite](#1-pre-requisite)
- [Install Azure CLI](#2-install-azure-cli)
- [AZ login](#3-az-login)
- [Create Data Factory](#4-create-data-factory)

### 1. Pre-Requisite
- As we know that Subscription & Resource Group are two mandatory requirements in-order to create any resource in Azure Cloud Service, we assume that we have already these created.
- An Service Principal must be created and assigned with required role & permission at the Resource Group (level) which we are going to use for the deployment.

#### 2. Install Azure CLI
- Install Azure CLI in Azure MV [CICD] (or) local machine. Run the below command to download & install Azure CLI into windows machine
```
$ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; rm .\AzureCLI.msi
```
> **Note:**
> - You need to run PowerShell as Administrator.
> - Once After installation, Restart the PowerShell terminal to make the changes effective.
- Verify your installation by running ```az --version``` command once after installation completed. you will get below result.

<p align="center">
  <img width="702" height="334" src="https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Resource%20Creation%20-%20%5BCLI%5D/images/install-azure-cli-on-windows.png?raw=true">
</p>

#### 3. AZ Login
- Connect to Azure CLI from powershell / command prompt. provide the below information when log into azure cli.
```commandline
az login [--allow-no-subscriptions]
         [--federated-token]
         [--identity]
         [--password]
         [--scope]
         [--service-principal]
         [--tenant]
         [--use-cert-sn-issuer]
         [--use-device-code]
         [--username]
``` 
- Authenticate via WEB-UI, This will open portal.azure.com where you need to authenticate using username & password.   
```commandline
az login
```

- Authenticate via CLI username & password.  
```commandline
az login -u user_name -p pass_word
```

> **Note:**
> - It is not recommended by Microsoft to use UserName & Password as primary option for more information please use below [link](https://github.com/AzureAD/microsoft-authentication-library-for-python/wiki/Username-Password-Authentication)

- Authenticate via CLI Service Principal & Client Secret.   
```commandline
az login --service-principal -u <app-id> -p <password-or-cert> --tenant <tenant>
```
> **Note:**
> - Base don my experience Service Principal's are the most preferable and secure way of authenticating with Azure AD. Instead using App secret we prefer using CERTIFICATE authentication.
- Once after successful login, you will get below screen as output.

<p align="center">
  <img width="1285" height="258" src="https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Resource%20Creation%20-%20%5BCLI%5D/images/az-login-windows.png?raw=true">
</p>

- Authenticate using Managed Identity. [Log in using a VM's system-assigned managed identity]   
```commandline
az login --identity
```   
or   
```commandline
az login --identity -u /subscriptions/<subscriptionId>/resourcegroups/myRG/providers/Microsoft.ManagedIdentity/userAssignedIdentities/myID
```

#### 4. Create Data Factory
- In order to create new data factory using azure cli, you can use the below command.   
```commandline
az datafactory create --factory-name
                      --resource-group
                      [--factory-git-hub-configuration]
                      [--factory-vsts-configuration]
                      [--global-parameters]
                      [--if-match]
                      [--location]
                      [--tags]
```
| Command | Status | Comments |
|---------|----------|----------|
| --factory-name | Required | Specifies the Data Factory name to be created.|
| --resource-group | Required | Specifies the RG name where to be created.|
| --factory-git-hub-configuration | Optional | Allows you to configure GitHub Repo details required such as [account-name, collaboration-branch, last-commit-id, repository-name, root-folder] |
| --factory-vsts-configuration | Optional | Allows you to configure Azure DevOps Repo details required such as [account-name, project-name, collaboration-branch, last-commit-id, repository-name, root-folder] |
| --global-parameters | Optional | Used to parse optimal parameters such as [debug, help, verbose & etc...] |
| --location | Optional | Specifies which region that the resource needs to be created, By default it will take the region as the RG's created region if not specified. |

> **Note:**
> - At a given time only one of the configuration can be used among *--factory-git-hub-configuration* & *--factory-vsts-configuration*. You cannot use both at the same time since both are Git Sources. 

**Create Data Factory [Default]**
```commandline
az datafactory create --resource-group rg-firststep-devtest-001 --factory-name adf-firststep-devtest-eastus2-002
```
> **Note:**
> - When you create data factory using azure CLI without giving --location parameter, by default it will inherit region from resource group.

**Create Data Factory [GitHub Configuration]**
```commandline
az datafactory create --resource-group rg-firststep-devtest-001 --factory-name adf-firststep-devtest-eastus2-002 --factory-git-hub-configuration account-name="FirstStep029" collaboration-branch="master" last-commit-id="" repository-name="adf-cli-dev" root-folder="/"
```

**Create Data Factory [VSTS (DevOps) Configuration]**
```commandline
az datafactory create --resource-group rg-firststep-devtest-001 --factory-name adf-firststep-devtest-eastus2-003 --factory-vsts-configuration account-name="First-Step-029" collaboration-branch="main" last-commit-id="" project-name="adf-test" repository-name="adf-test" root-folder="/" --location "East US2"
```


### Reference:
> [[ADF] - Naming Convention](https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Best%20Practice%20%26%20Recommendations.md#1-naming-convention)  
> [[ADF] - Limitations](https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Limitations.md#limitations)  