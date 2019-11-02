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
11. Repository Pattern
12. Project architecture
13. Actionresult and IActionresult
14. Forms authentication
 Use of acceptverbs
 Same actionresult with get and post and same signature how you handle the request
 Actioname attribute
 Mvc life cycle
 Static class
 Extension methods
 Design pattern
 Solid principles
 Validate.js
 Unobtrustive.js usage
 Service layer authentication
 Usage of interface
 Dependency injection
 Which dll you use for dependency injection in nuget
 Parllell task execution
 Unit container
 Value and reference type
 String in value or reference type
 Optinal parameters
 Int is what type
 Exception action filters
 Class and struct
 When to use this
 Write a code for injecting a interface in your class
 How to ensure that there is only one instance for singleton class
 Use of finally
 Write a code for async and await
 Abstract class and interface
 Garbage collections
 When to use abstract and interface?
 Enums
 String and string buffer
 Write a code for inheritance
 Override and virtual usage
 Stored procedures
 Triggers
 While passing token what will be key name and value in body header
 .net core authentication
 Handle mime in api
 Injecting httpcontext
 Cors
 Linq and lambda exp
 Claims and principal
 Usage of serilog nlog
 Ilogger
 Logger
 Common logging
 Log4net
 How you will save logs in database
 Sql 2016 features
 Configuration file read
 How you read data from config file value in c# code
 Usage of resx file  

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