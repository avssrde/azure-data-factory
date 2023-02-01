# Create Azure Blob Storage Linked Service using Azzount Key

- [Create Azure Blob Storage Linked Service using Azzount Key](#create-azure-blob-storage-linked-service-using-azzount-key)
    - [1. PreRequsite](#1-prerequsite)

### 1. PreRequsite
Inorder to create a linked service that connects to Azure Blob Storage you need to have the below listes items created/configured.

- Resources:
  - Azure Data Factory
  - Azure Blob Storage
  - Azure Key Vault
- Configurations:
  - Enable **system assigned managed identity** in ADF -> Settings -> Managed Identities -> System assigned (tab)
  - Add ADF to Access Policies in Azure Key Vault as follows AKV -> Access Policies.
  - **Interactive Authoring** must be enabled in **AutoResolveIntegrationRuntime**.
  - Create secret for connection string (or) account key obtained from blob storage