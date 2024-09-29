Comparisons: AWS Secrets Manager vs Systems Manager Parameter Store

![image](https://github.com/user-attachments/assets/895f7f0e-b76e-4eb3-9f6f-82af178692f2)


Awesome Cloud — AWS Secrets Manager vs Parameter Store (Systems Manager)

AWS gives you two ways to store and manage application configuration data centrally:

Secrets Manager: It was designed specifically for confidential information (like database credentials, API keys) that needs to be encrypted, so the creation of a secret entry has encryption enabled by default. It also gives additional functionality like rotation of keys.
Systems Manager Parameter Store: It was designed to cater to a wider use case, not just secrets or passwords, but also application configuration variables like URLs, Custom settings, AMI IDs, License keys, etc.
Similarities
Encryption
Both Secrets Manager and Parameter Store can leverage AWS KMS to encrypt values. By using KMS, IAM policies can be configured to control permissions on which IAM users and roles have permission to decrypt the value. Though access to the values can be restricted through IAM, encryption provides an additional layer of security and is sometimes required for compliance.

Key/Value Store
Both services allow you to store values under a name or key.
Both allow the keys to having prefixes. For example, parameters or secrets can be put in the following prefix schema application/environment/parametername or any other combination of prefixes that meets the need of the application. This is useful since the deployment of the application can reference different parameters/secrets based on the deployment environment.

CloudFormation Integration
CloudFormation is used as an Infrastructure as a code (IaC) model, and storing secrets in CloudFormation is a bad security practice. You can store the secrets (e.g. Database username and password) in Parameter Store or Secrets Manager which can be referenced in the CloudFormation template so that you just have a pointer to the value in your template instead of containing the secrets in plaintext.

Versioning
Both services support versioning of secret values. This allows you to view previous versions of your parameters of secret in case you needed them. You can choose to restore the older version of the parameter.
Parameter Store only allows one version of the parameter to be active at any given time.
Secrets Manager allows multiple versions to exist at the same time when you are performing a secret rotation using the staging labels.

Key Differences
Cost
Secrets Manager: It is paid. The storage cost is $0.40 per secret per month and API interactions cost is $0.05 per 10,000 API calls.

Parameter Store: For Standard parameters, No additional charge for storage and standard throughput. For higher throughput, API interactions cost is $0.05 per 10,000 API calls.
For Advanced parameters, storage cost is $0.05 per advanced parameter per month and API interactions cost is $0.05 per 10,000 API calls.

Secrets Rotation
Secrets Manager: It offers the ability to switch secrets at any given time and can be configured to regularly rotate depending on your requirements. It provides full key rotation integration with few AWS service like RDS, Redshift, DocumentDB. For other services, AWS allows you to write custom key rotation logic using an AWS Lambda function.

Parameter Store: You can write your own function that updates credentials managed by Parameter Store, and invoking it via a CloudWatch scheduled event or Eventbridge.

Cross-account Access
Secrets Manager: Secrets can be accessed from another AWS account. It easier to share the secrets cross-accounts. This is useful if secrets are centrally managed from another AWS account or beneficial for use cases where a customer needs to share a particular secret with a partner.

Parameter Store: Not supported.

Secret Size
Secrets Manager: It can store up to 10KB secret size.

Parameter Store: Standard Parameters can store up to 4096 characters (4KB size) for each entry, and Advanced Parameters can store up to 8KB entries.

Limits
Secrets Manager: It has a limitation of storing 500,000 secrets per region per account.

Parameter Store: It has a limitation of storing 10,000 standard parameters per region per account.

Multiple Regions Replication
Secrets Manager: It lets you easily replicate your secrets in multiple AWS Regions to support applications spread across those Regions as well as disaster recovery scenarios.

Parameter Store: It doesn’t support cross region replication out of the box.

Use Cases
Choose Secrets Manager if:
You want to store only encrypted values and super easy way to manage the rotation of the secrets. For instance, for organizations that have to be PCI compliant where the mandate is to rotate your passwords every 90d, AWS Secrets Manager makes that a very easy and seamless process.
Choose Parameter Store if:
You want cheaper option to store encrypted or unencrypted secrets.



Alternatives

Hashicorp Vault:

HashiCorp Vault is an identity-based secrets and encryption management system. It provides encryption services that are gated by authentication and authorization methods to ensure secure, auditable and restricted access to secrets. It is used to secure, store and protect secrets and other sensitive data using a UI, CLI, or HTTP API.

A secret is anything that you want to tightly control access to, such as tokens, API keys, passwords, encryption keys or certificates. Vault provides a unified interface to any secret, while providing tight access control and recording a detailed audit log.

API keys for external services, credentials for service-oriented architecture communication, etc. It can be difficult to understand who is accessing which secrets, especially since this can be platform-specific. Adding on key rolling, secure storage, and detailed audit logs is almost impossible without a custom solution. This is where Vault steps in.

Vault validates and authorizes clients (users, machines, apps) before providing them access to secrets or stored sensitive data.

How Vault Works

How does Vault work?
Vault works primarily with tokens and a token is associated to the client's policy. Each policy is path-based and policy rules constrains the actions and accessibility to the paths for each client. With Vault, you can create tokens manually and assign them to your clients, or the clients can log in and obtain a token. The illustration below displays Vault's core workflow.

Vault Workflow

The core Vault workflow consists of four stages:

Authenticate: Authentication in Vault is the process by which a client supplies information that Vault uses to determine if they are who they say they are. Once the client is authenticated against an auth method, a token is generated and associated to a policy.
Validation: Vault validates the client against third-party trusted sources, such as Github, LDAP, AppRole, and more.
Authorize: A client is matched against the Vault security policy. This policy is a set of rules defining which API endpoints a client has access to with its Vault token. Policies provide a declarative way to grant or forbid access to certain paths and operations in Vault.
Access: Vault grants access to secrets, keys, and encryption capabilities by issuing a token based on policies associated with the client’s identity. The client can then use their Vault token for future operations.
Why Vault?
Most enterprises today have credentials sprawled across their organizations. Passwords, API keys, and credentials are stored in plain text, app source code, config files, and other locations. Because these credentials live everywhere, the sprawl can make it difficult and daunting to really know who has access and authorization to what. Having credentials in plain text also increases the potential for malicious attacks, both by internal and external attackers.

Vault was designed with these challenges in mind. Vault takes all of these credentials and centralizes them so that they are defined in one location, which reduces unwanted exposure to credentials. But Vault takes it a few steps further by making sure users, apps, and systems are authenticated and explicitly authorized to access resources, while also providing an audit trail that captures and preserves a history of clients' actions.

The key features of Vault are:

Secure Secret Storage: Arbitrary key/value secrets can be stored in Vault. Vault encrypts these secrets prior to writing them to persistent storage, so gaining access to the raw storage isn't enough to access your secrets. Vault can write to disk, Consul, and more.

Dynamic Secrets: Vault can generate secrets on-demand for some systems, such as AWS or SQL databases. For example, when an application needs to access an S3 bucket, it asks Vault for credentials, and Vault will generate an AWS keypair with valid permissions on demand. After creating these dynamic secrets, Vault will also automatically revoke them after the lease is up.

Data Encryption: Vault can encrypt and decrypt data without storing it. This allows security teams to define encryption parameters and developers to store encrypted data in a location such as a SQL database without having to design their own encryption methods.

Leasing and Renewal: All secrets in Vault have a lease associated with them. At the end of the lease, Vault will automatically revoke that secret. Clients are able to renew leases via built-in renew APIs.

Revocation: Vault has built-in support for secret revocation. Vault can revoke not only single secrets, but a tree of secrets, for example all secrets read by a specific user, or all secrets of a particular type. Revocation assists in key rolling as well as locking down systems in the case of an intrusion.
