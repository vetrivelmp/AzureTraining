# Implement Azure Security
- What is Azure AD?
- Quick look at Azure AD users
- Role Based Access Control
- Introduction to Application Object
  - Use Case: Read data from Storage account using application object
  - Create app object and give rights to it on storage account - Reader, Storage Blob Data Reader
- What is the Azure Key Vault Service?
- Azure Key Vault - What is a service principal
- Azure Key vault - Secrets
- Azure Key vault - Encryption keys
- Azure VM Disk Encryption
  - Create encryption key in key vault
  - Enable Access policy in key vault - "Azure Disk Encryption for volume encryption"
  - Open VM\Disks\Additional Settings
  - Disks to Encrypt: OS and data disk
  - Select key from key vault
- Azure Key Vault Secrets - Using Application Objects
  - Refer
    - 227-azure-key-vault-secrets-using-application-object
  - Create app object, give rights to app object on key vault, create secret in key vault, update app object values in source code and run it

- Managed Service Identity
  - 231-managed-identities-example-on-not-using-managed-identies
  - 232-managed-identities-using-identities
  - 233-azure-key-vault-secrets-using-managed-identity
  - 234-managed-identity-getting-the-access-token

- Primer to OAuth and OpenID Connect - History of Authentication
- Primer to OAuth and OpenID Connect - Identity Provider
- What is OAuth?
- OAuth 2.0 Authorization Code Flow
- OAuth 2.0 Implicit Flow
  - When both auth code and access token both comes from the broser
  - Useful when all code is client side - Angular JS, Java script etc
- OAuth 2.0 - Overview
- OAuth with Azure AD - Overview
- Quick Look into OAuth when logging into Azure
- OAuth 2.0 for ASP.Net Core
- The Access Tokens
- OAuth 2.0 - Accessing Blob storage
- Azure AD - Multi-Factor Authentication
- OpenID Connect
  - Built on the OAuth 2.0 protocol and uses an additional JSON Web Token (JWT)
  - An identity layer built on top of the OAuth 2.0 framework
  - It allows third-party applications to verify the identity of the end-user and to obtain basic user profile information.
  - It is not controlled by any one website or service provider
  You control how much personal information you choose to share with websites that accept OpenIDs

## Using Postman to access Azure Blob
- Refer: https://www.getpostman.com/collections/cbd4a3b4c7cb8fe7d828
- Create app object in AAD named - Postman
- Open app object and copy endpoint - OAuth 2.0 token endpoint (v1)
- Open Postman tool
- Make a Get Request and paste the endpoint URL
- Open Headers
  - Content-Type: application/x-www-from-urlencoded
- Open Body
  - Form Data
    - grant_type: client_credentials
    - client_id:
    - client_secret:
    - resource: https://storage.azure.com
- Click Send
- Copy access token returned
- From Storage Account copy the URI of Blob which we want to download
- Create another get request using Postman tool and paste this URI
- Open Headers
  - Authorization: Bearer <Paste access token>
  - x-ms-version: 2017-11-09
- Click Send


## Using Postman to access Keyvault Secret
- Refer: https://www.getpostman.com/collections/cbd4a3b4c7cb8fe7d828
- Create Key Vault - https://appkvatinjune21.vault.azure.net/
- Create secret named - secret
- Access Policy
  - Allow app object to Get secret
- Open Postman Tool and change below details to get Access Token for Keyvault
  - resource: https://vault.azure.net
- Click Send
- Copy access token
- Copy secret URL
- Also need to append below string in URL
  - ?api-version=7.1
  - https://appkvatinjune21.vault.azure.net/secrets/secret/3faab0197b70458391e00d3905504e2b?api-version=7.1
- Create a new Get Request
- Paste URL
- Add header
  - Authorization: Bearer <Paste access token>
  - x-ms-version: 2017-11-09

- Click Send
