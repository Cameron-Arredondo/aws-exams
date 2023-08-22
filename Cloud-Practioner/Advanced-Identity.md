# AWS STS (Security Token Service)
- AWS STS enables you to create temporary limited-privileges credentials to access your AWS resources
- Short-term credentials: you configure expiration period
How is this done?
The user will assume the role using an STS api call. 
Use cases:
-  Identity Federation: manage user identities in external systems, and provide them with STS tokens to access AWS resources
- IAM roles for cross/same account access
- IAM roles for EC2 instances, provide temporary credentials for EC2 instances to access AWS resources

## AWS Cognito
- Provide identity for web and mobile app users, we would not want create IAM users for them.  
- Cognito will have a DB of users that can authenticate to the web or mobile app without using IAM roles to access the resources (application).
## Microsoft Active Directory
- Found on any Windows Server that has AD domain services
- Database of objects: User Accounts, Computers, Printers, File Shares, Security Groups
- Centralized security management, create account and assign permissions

AWS Directory Services can extend Active Directory:
- AWS Managed Microsoft AD: can establish trust connection with on premise AD
- AD connector: Directory Gateway (proxy) to redirect to on-premise AD, supports MFA. Users are managed on the on-premise AD
- Simple AD: Standalone directory in the cloud, cannot connect to on-prem

## AWS IAM Identity Center (Successor to AWS SSO):
- One login for all AWS account in your AWS organizations
- Single pane of glass for all accounts in your org.

Identity Providers:
- There is a built in identity store in IAM Identity center
- 3rd Party: AD, OneLogin, Okta

