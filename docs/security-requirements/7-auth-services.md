# 7 Authorization Services

In order to enable the delivery of GovStack use cases, a mechanism must be defined that provides the appropriate level of access to the various building blocks by different users and organizations. This includes defining information sharing across service or organizational boundaries, enforcing appropriate roles and permissions for users, allowing user session information to be passed between building blocks, and enforcing secure access between Building Blocks (either co-located within a service, or across applications/organizations using an Information Mediator).

_Note: Additional technical detail and example scenarios can be found in this_ [Authentication and Cross-BB Authorization](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/239370263/Authentication+and+Cross-BB+Authorization) _document_&#x20;

### 7.1 Key Requirements <a href="#key-requirements" id="key-requirements"></a>

* Authentication and IAM/Roles/Permissions should be managed by an Authorization Service (functionality extracted from current Security spec) using well-defined standards like OpenID Connect (OIDC).
  * This service will handle login, defining roles and permissions, and returning a set of roles/permissions for a user session
  * This service may be implemented as a standalone Building Block or as part of the Application that is controlling the user flow.
* After user login and retrieval of roles/permissions for that user
  * The Application is responsible for managing any outbound calls based on the roles/permissions for that user - whether to internal BBs or cross-organizational requests through IM.
  * The Application will manage the API keys/credentials needed to access any local BB APIs that it calls
  * We _will not_ pass user/session information when making API calls to local BBs
  * We _will not_ pass JWT tokens or roles when making API calls through Information Mediator
* JWT/tokens need to be exchanged between different UIs/applications - If we need to pass control over to another app to fill in some information (giving consent, etc) - use OIDC
* The Information Mediator is used to facilitate communication between different organizations. The authorization and level of access is defined at the organization level, not the user level (ie. this particular organization has permission to access this set of data)
  * The security server will hold/manage credentials and API keys that are needed for accessing remote services
  * An organization can also allow access to an individual user based on a foundational ID
* IM is needed when going outside of a local network (ie. across the internet)

### **7.2 Accessing the API of an existing DPG or Product which is functioning as a Building Block:**

* Set up an account/set of credentials in the other DPG/application that allows access to the APIs
* The authorization services (either within the application or separate functionality) will hold the login credentials in some type of secret storage (.env file or similar mechanism)
* When calling an API in the DPG, the Application should first call the DPG login API (there must be an API exposed for login) and then hold the token that is needed for API calls
* The Application will pass the appropriate token on subsequent API calls to the DPG

### 7.3 User Role and Permission Management

Within a GovStack implementation, an Identity and Access Management (IAM) or Role-Based Access Control (RBAC) system must be in place. This will define the level of access and permissions that a particular user (or group of users) will have within the GovStack system. The requirements for IAM/RBAC are described in Section 8.2 of this security specification&#x20;

### 7.4 Definitions <a href="#definitions" id="definitions"></a>

**Service**: An API or endpoint provided by a Building Block or internal microservice of the Application

**Application**: One or more Building Blocks that may be combined with a UI and/or internal services which implement some business logic to provide a set of related services.

**Use Case/User Journey:** A system involving one or more UX components that allows a user to access multiple services which may be co-located or require the use of an information mediator to access a set of services/applications.

**Organization**: An entity that maintains one or more applications or services that may be consumed by other organizations

**User**: An individual that is accessing a particular application or set of services

**Information Mediator**: Connects applications across the internet, allowing services that are owned by different organizations to share data securely and using agreed-upon rules

**Foundational Identity**: a unique identifier for an entity that corresponds with a national identification system

**Functional Identity**: a login or user account that is associated with a particular application or set of services

**Session**: a set of information (or token) that provides context to a particular user interaction with an application (ie. keeping track of a logged-in user and what they have permission to do while they are logged in for a particular period of time)
