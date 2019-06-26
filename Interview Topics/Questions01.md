# Part 1

1. Web API Authentication
2. CSRF attacks handling
3. SQL Injection
4. Validate Anti-forgery token
5. Attribute based routing 
6. Action filters
7. Async and await
8. var vs dynamic
9. Interface with same methods
10. Polymorphism

### Web API Authentication

* Web API project template gives you three options for authentication:

    1. Individual accounts. The app uses a membership database.
    2. Organizational accounts. Users sign in with their Azure Active Directory, Office 365, or on-premise Active Directory credentials.
    3. Windows authentication. This option is intended for Intranet applications, and uses the Windows Authentication IIS module.

* Authentication is knowing the identity of the user. Authorization is deciding whether a user is allowed to perform an action.
* Integrated Windows authentication enables users to log in with their Windows credentials, using Kerberos or NTLM. The client sends credentials in the Authorization header. Windows authentication is best suited for an intranet environment.

### CSRF attacks handling

* CSRF attacks are possible against web sites that use cookies for authentication, because browsers send all relevant cookies to the destination web site.
* 