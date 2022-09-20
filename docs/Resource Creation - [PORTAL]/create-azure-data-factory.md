# Create new Azure Data Factory

### Table Of Contents
- [Basics](#basics)
- [Git Configuration](#git-configuration)
- [Networking](#networking)
- [Advanced](#advanced)

### Basics:
- All the Properties & Configurations inside basic tab is mandatory.
- Config & Props:
    - **Subscription:** You must choose an existing & active azure subscription, Since each ADF must be created inside an subscription.
    - **Resource Group:** You must choose an existing RG or you can create an new RG and map it with ADF.
    - **Name:** You must give an unique name as per the naming convention [guidence](https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Best%20Practice%20%26%20Recommendations.md#11-data-factory) provided by Microsoft.
    - **Region:** You must choose which region that ADF needs to be deployed. More details on Region and other associated properties can be found [here](https://azure.microsoft.com/en-in/global-infrastructure/geographies/#geographies)

### Git Configuration:
- ADF can be easily integrated with Git Repository. It currently supports 2 types of Git provider as listed below.
- Git Repo Types:
    - Azure DevOps Git
    - GitHub (or) GitHub Enterprise
> **Note:** This is an Optional Configuration which can be configured later once Data Factory is created. By enabling the '*Configure Git Later*' check box you can configure the repo once after ADF is created.
- Configuration [Azure DevOps]:
    - **Account:** Github Account name where the repo is located.
    - **Project Name:** Name of the existing Azure DevOps project.
    - **Repo Name:** Name of the existing repo which needs to be mounted.
    - **Branch:** Name of the existing branch which will be used as collaboration branch.
    - **Root Folder:** Location in the collaboration branch where the entitied will be created & stored. "/" indicated the root folder.
- Configuration: [GitHub (or) GitHub Enterprise]
    - **Account:** Github Account name where the repo is located.
    - **Name:** Name of the existing repo which needs to be mounted.
    - **Branch:** Name of the existing branch which will be used as collaboration branch.
    - **Root Folder:** Location in the collaboration branch where the entitied will be created & stored. "/" indicated the root folder.

### Networking
- This Tab will allow you to configure and control network configuration used for '*Self Hosted IR*'
- **Manged Virtual Network**:
    - Creating an IR with in Azure managed virtual network uses private endpoints to securely connect to supported data stores.
    - managed virtual network ensures the data integration process is isolated and secure.
    - Benefits:
        - Don't need to create a subnet for an integration runtime
        - Deep Azure networking knowledge isn't required.
        - A managed virtual network along with managed private endpoints protects against data exfiltration.
    > **Note:**   
    > - Currently, the managed virtual network is only supported in the same region as the Data Factory region.  
    > - An existing global integration runtime can't switch to an integration runtime in a Data Factory managed virtual network and vice versa.

### Advanced
- This Section will allow you to configure Customer Manged Encryption keys with in Data Factory.
- **Encryption:**
    - By default, data is encrypted with a randomly generated Microsoft-managed key.
    - This key is uniquely assigned to your data factory.
    - **BYOL:**
        -  For extra security guarantees, you can now enable Bring Your Own Key (BYOK) with customer-managed keys feature in Azure Data Factory. 
    - When customer-managed key enabled, Data Factory uses both the factory system key and the CMK to encrypt customer data.
    > **Note:**
    > - Missing either key would result in Deny of Access to data and factory.
    > - You must store the CMK in *Azure Key Vault*
    > - Key vault and Data Factory must be in the same Azure Active Directory (Azure AD) tenant and in the same region, but they may be in different subscriptions.
- You can enable CMK by enabling the check box in Advanced tab.
- Then you may need to fill below listed properties.
    - **Key Vault URL:** Key Vault URL with test key and value.
    - **User Assigned Identity:** This allow you to communicate with KeyVault you have specified in Vault URL.


### Reference:
> [[ADF] - Naming Convention](https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Best%20Practice%20%26%20Recommendations.md#1-naming-convention)  
> [[ADF] - Limitations](https://github.com/FirstStep029/auzre-data-factory/blob/master/docs/Limitations.md#limitations)  