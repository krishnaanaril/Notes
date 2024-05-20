## Understand Microsoft Entra ID

- **Microsoft Entra ID** is a comprehensive solution for managing identities, enforcing access policies, and securing your applications and data in the cloud and on-premises.
- AD DS (Active Directory Domain Services) is a directory service that provides the methods for storing directory data, such as user accounts and passwords, and makes this data available to network users, administrators, and other devices and services. 
- AD DS runs as a service on Windows Server, referred to as a domain controller.
- The term tenant in this context typically represents a company or organization that signed up for a subscription to a Microsoft cloud-based service such as Microsoft 365, Intune, or Azure, each of which uses Microsoft Entra ID.
-  Within an Azure subscription, you can create multiple Microsoft Entra tenants.
- At any given time, an Azure subscription must be associated with one, and only one, Microsoft Entra tenant. But you can associate the same Microsoft Entra tenant with multiple Azure subscriptions. 
- The lack of support for the traditional computer domain membership means that you can't use Microsoft Entra ID to manage computers or user settings by using traditional management techniques, such as Group Policy Objects (GPOs).
- Microsoft Entra ID doesn't include the organizational unit (OU) class, which means that you can't arrange its objects into a hierarchy of custom containers, which is frequently used in on-premises AD DS deployments. 
- Deploying AD DS on an Azure virtual machine requires one or more extra Azure data disks because you shouldn't use drive C for AD DS storage. These disks are needed to store the AD DS database, logs, and the sysvol folder. 
- You can't query Microsoft Entra ID by using LDAP; instead, Microsoft Entra ID uses the REST API over HTTP and HTTPS.
- Microsoft Entra ID doesn't use Kerberos authentication; instead, it uses HTTP and HTTPS protocols such as SAML, WS-Federation, and OpenID Connect for authentication, and uses OAuth for authorization.
- Microsoft Entra ID can provide users with an SSO experience when using applications such as Facebook, Google services, Yahoo, or Microsoft cloud services.
- The following features are available with the Microsoft Entra ID P1 edition:
    1. Self-service group management.
    2. Advanced security reports and alerts.
    3. Multi-factor authentication.
    4. Enterprise SLA of 99.9%.
    5. Password reset with writeback.
    6. Cloud App Discovery feature of Microsoft Entra ID
    7. Conditional Access based on device, group, or location
    8. Microsoft Entra Connect Health
- In addition to these features, the Microsoft Entra ID P2 license provides extra functionalities:
    1. Microsoft Entra ID Protection
    2. Microsoft Entra Privileged Identity Management
- By using Microsoft Entra Domain Services, you can freely migrate applications that use LDAP, NTLM, or the Kerberos protocols from your on-premises infrastructure to the cloud. 
-  Microsoft Entra ID P2 edition provides additional identity protection features, such as risk-based conditional access.
