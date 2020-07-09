# Account Management Concepts



#### Tenant

A tenant is how OSIsoft Cloud Services (OCS) refers to a customer, client, or organization. Before a customer can use OCS, a tenant must be provisioned for them. A customer will have at least one tenant and could have more than one tenant and each tenant has at least one identity provider associated with it. 

#### Namespace

Namespaces are logical organizations of data. A namespace is the target destination for data sent to OCS. Namespaces are used to separate and contain data, configure regions [QUESTION: Aren't regions another way of segregating data?], and creating environments for development and testing.

When a namespace is created, a set of Osisoft Cloud Services (OCS) data services (for example, SDS and Asset service) and the storage space allocated to support those services is deployed to the namespace. Each namespace is distinct and separate from other namespaces and, therefore, they isolate the resources contained within it. The resources are scoped to the namespace. Therefore, you can create an SdsType or an SdsStream object with the same name in two different namespaces.

Namespaces are provisioned to a particular region and are scoped to that region. 

Data is stored in a namespace. Data cannot be directly copied or moved between namespaces. Nor can it be copied or moved from one region to another. To copy or move data, the data must be copied or exported out of OCS and then imported to the new namespace. 

A tenant is divided into one or more namespaces.

#### User

Authentication of individuals is managed by the identity provider associated with the tenant. When a user logs in to Osisoft Cloud Services (OCS), they authenticate themselves with an identity provider such as Google or Azure Active Directory.

The Account Administrator user creates users and assigns roles to them. These roles determine what objects a user has access to and what they are authorized to do with these objects. Roles are managed through the Access Control List. See [Roles](#roles) for more information.

#### Client

Clients are applications and adapters, acting on behalf of users, that allow for programmatic access to the Osisoft Cloud Services (OCS) APIs. The following client types are supported in OCS:

- Client credential clients &#150; Used for server-to-server communications without the presence or intervention of a user. Examples include OSIAdapter or Edge Data Store sending data to OCS. The client credentials client is issued a client ID and secret. Once authenticated, it is granted an access token with a defined lifetime. The tokens may either be short-lived access tokens or longer-lived refresh tokens that allow the client to request new access tokens. 
- Authorization code clients &#150; Used by web-based applications, native mobile applications, and desktop applications that access OCS, this client type requires user interaction. Users authenticate with the Identity Provider. This client supports silent refresh, which allows the user to automatically receive a new access token, providing for uninterrupted access to the application.
- Hybrid clients &#150; Used by thick client applications, this client requires user interaction. The user authenticates with the Identity Provider. Once the user is authenticated, then the server-side client steps in and server-to-server communication commences. Refresh tokens and access tokens are granted to the server-side client, requiring no further user interaction.

Clients are assigned roles that define their access to OCS objects. See [Roles](#roles) for more information. 

#### <a name="roles"></a> Roles

The Account Administrator creates an Access Control List (ACL) entry for each OCS entity (namespaces, streams, and so on) that defines access permissions for specific roles. Users and clients are assigned to one or more roles that define their access to OCS objects and the actions they can perform on these objects. 

OCS provides two built-in roles:

- Account member &#150; Assigned to every user and client credentials client. Users and clients assigned this role can access objects or information of which they are the owner.
- Account Administrator &#150; Role with the highest privileges, the Account Administrator can create and delete users, clients, and secrets.


