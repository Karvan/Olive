# ClaimsPrincipal Extension Methods
>A `claim` is a statement that one subject makes about itself or another subject. The statement can be about a name, identity, key, group, 
privilege, or capability, for example. `Claims` are issued by a provider, and they are given one or more values and then packaged in security 
tokens that are issued by an issuer, commonly known as a `security token service (STS)`. For a full list of definitions of terms associated 
with `claims-based identity`, see “Claims-Based Identity Term Claims-based identity isn’t new. It’s been in use for almost a decade.
Definitions” at http://msdn.microsoft.com/en-us/library/ee534975.aspx.
You can use claims to implement `role-based access control (RBAC)`. Roles are claims, but `claims` can contain more information than just 
role membership. Also, you can send claims inside a signed (and possibly encrypted) `security token` to assure the receiver that they 
come from a trusted issuer.

> Note:You should use `HttpContext.Current.User.` Or use the `User` property inside a `Controller` action method.


## GetEmail()
#### When to use it?
When you want to use the `Email` claim of current user Email in your applications.

#### Example:

```csharp

 HttpContext.Current.User.GetEmail(); // returns current user Email 
```
Or

```csharp

User.GetEmail(); // returns current user Email inside a `Controller` action method.
```


## GetId()
#### When to use it?
When you want to use the `NameIdentifier` claim of current user Email in your applications.
#### Example:

```csharp

HttpContext.Current.User.GetId(); // returns current user NameIdentifier
```

Or

```csharp

User.GetId(); // returns current user NameIdentifier inside a `Controller` action method.
```

##GetRoles()
`Roles` are `claims`, but `claims` can contain more information than just role membership.
#### When to use it?
This method return a list of Roles which current user has.
#### Example:

```csharp

IEnumerable<string> roles;
roles = HttpContext.Current.User.GetRoles(); //returns roles of current user 
foreach (var item in roles)
{
 ...
}
```

Or

```csharp
IEnumerable<string> roles;
roles = User.GetRoles(); //returns roles of current user inside a `Controller` action method.
foreach (var item in roles)
{
 ...
}
```


## GetFirstIssuer()
`Claims` are issued by a provider, and they are given one or more values and then packaged in security tokens that are issued by an issuer, commonly known as a `security token service (STS)`
#### When to use it?
When you want to know the `Issuer` in your applications.
#### Example:

```csharp

HttpContext.Current.User.GetFirstIssuer(); // returns current Issuer, for example the name of your Application
```

Or

```csharp

User.GetFirstIssuer(); // returns current Issuer, for example the name of your Application inside a `Controller` action method.
```

>Note: The following table shows the relationships between security tokens, claims, and issuers (A Guide To Claims-Based Identity And Access Control published by Microsoft):

|Security token                 |Claims                       |Issuer         |
|-------------------------------|-----------------------------|---------------|
|Windows token. This token is represented as a security identifier (SID). This is a unique value of variable length that is used to identify a security principal or security group in Windows operating systems.|User name and groups.| Windows Active Directory domain.|
|User name token.| User name.| Application.|
|Certificate.| Examples can include a certificate thumbprint, a subject, or a distinguished name.|Certification authorities, including the root authority and all authorities in the chain to the root.|
