# 8 Additional Security Modules

Any Building Block must follow the security requirements that are outlined in the Cross-Cutting Requirements section of this document. In addition, specific security related functionality should be provided in any GovStack implementation. An API Gateway may be provided to manage communication between building blocks as well as any incoming requests from external systems. The API Gateway will work with the Information Mediator Building Block and provide additional controls and security while coordinating API calls between the application and various Building Blocks.

_Note: The API Gateway functionality is connected to the GovStack Adaptor concept which is described in_ [_Section 6 (Onboarding Products) of the Non-Functional Requirements document_](../architecture-and-nonfunctional-requirements/6-onboarding.md)

Second, some type of Identity and Access Management or Role-Based Access Control should be implemented as part of a GovStack solution, as desribed in Section 7.4 of this Security specification.

The functional requirements for both of these components are described below.

### 8.1 API Management and Gateway Functional Requirements

Although API Management and Gateway services are an architectural element, this section of the document also describes the detailed functional requirements for implementing API management, governance and gateway services for GovStack. Explicitly, the communications between all building blocks (BB’s) and applications shall be via open API based access.

The goal of this endeavor is to address primary security concerns centrally and create a consistent way of implementing a modern cloud-ready architecture to publish API’s to 3rd parties (both internal and external), govern and manage the access to API’s both internally and externally by policy and create centralized and secure point of access to each and every API endpoint exposed through GovStack. These functional requirements do not define specific APIs (API’s themselves are implemented by [other building blocks](../building-blocks/security-requirements/broken-reference/)<mark style="color:blue;">)</mark> - these functional requirements only define the functionality that must be implemented within the bounds of the security building block and how it needs to be applied to other building blocks.

**8.1.1 Multiple API Gateway (REQUIRED)**

The ability to implement segregated gateways for both internal and external API traffic. This means that the internal API driven integration traffic and the external API access traffic is to be segregated into separate gateway infrastructure components and access controlled by networks and network access policy.

**8.1.2 Standards Based Identity and Access (REQUIRED)**

The ability to implement standardized authentication, authorization and encryption protocols including federated identity (OAuth2, OpenID Connect, SAML2, SSO, SSL, TLS etc.). These standards MUST be supported and incorporated into any chosen API Management product out-of-the-box for controlling access to API interfaces.

Note that the native API interfaces for each building block's components may be implemented in clear text with no authentication and/or encryption etc. so long as the access to these interfaces is firewalled by network and network policy such that it is ONLY accessible through the API Gateway. This is intended to simplify, standardize and expedite API development, deployment and management.

Note that the APi interface specifications for the APi gateway and API management services are based on open standards based identity and access which is in turn based on OpenAPI 3.0. The following link describes how OAuth2 is used in OpenAPI 3.0 standards based identity and access: [https://swagger.io/docs/specification/authentication/oauth2/](https://swagger.io/docs/specification/authentication/oauth2/). It is this style of standards based identity and access that is required to be supported, Note that additional API interfaces may be exposed by the API Management and Gateway solution but they would predominantly be targeted for incorporation into the DevOps CI/CD tool chain not exposed to other BBs.

**8.1.3 Identity Store Plugins (REQUIRED)**

The ability to utilize separate identity stores as repositories for identity and perform proxied authentication to such repositories (for example LDAP) using multiple credentials including digital identity certificates.

**8.1.4 API Protection Features (REQUIRED)**

The ability to support many security and protection features such as Standard API keys, App-ID key pair, IP address filtering, Referrer domain filtering, Message encryption, Rule-based routing, Payload security, Channel security, Defense against common XML and JSON attacks, Low- to no-code security configuration, PCI compliance.

Note that this is not an exhaustive list and additional policy protection features may strengthen the value of any given solution.

**8.1.5 Centralized API Policy Based Access (REQUIRED)**

The ability to implement policy based access management for API endpoints. The policy MUST be able to be implemented centrally then applied across multiple gateways and all API endpoints.

**8.1.6 API Endpoint Transformation (REQUIRED)**

The ability to support multiple standards for proxying endpoints and exposing them as standard OpenAPI endpoints (see [Ref 1)](https://docs.google.com/document/d/1ePo98eu0Z4wKd-Ce522Zwpr9MOeNJeUw/edit#heading=h.4ost5vnqtuzo) including transformations such as XML ↔ JSON and SOAP ↔ REST

Note that this is not an exhaustive list of the required transformations and that additional transformations may reinforce the strength of a solution’s flexibility and adaptability.

**8.1.7 Alternative API Protocols (REQUIRED)**

The ability to support multiple common protocols such as JMS, WS, MQTT.

Note that this is not an exhaustive list and that additional alternative protocols supported may strengthen the value of the proposed solution.

**8.1.8 API Versioning and Lifecycle (REQUIRED)**

The ability to support multiple API versions and control multiple API versions and API lifecycle management.

Note that there are many potential features available to strengthen the solution proposition such as version dependency management and deployment rollback etc.

**8.1.9 API Call Traffic Shaping (RECOMMENDED)**

The ability to implement traffic transformation and traffic shaping. This is typically implemented as single/dual rate, private (per node) and shared (by multiple nodes) shapers.

Note that additional traffic shaping capabilities may strengthen the solution proposition.

**8.1.10 API Call Rate Limiting (REQUIRED)**

The ability to implement rate limiting for API calls on an API-by-API basis. This limits the rate at which API’s can be called by a consumer (for example 100/second etc.) and usually has many flexible options and caters for policy driven rate limits based on busy times etc. Principally it comes down to the offered SLA.

Support for complex SLA construction may strengthen the solution proposition.

**8.1.11 API Call Quotas (RECOMMENDED)**

The ability to implement quotas for API calls from specific clients (daily, weekly, monthly etc.). This restricts the number of API calls a client can make and also often includes flexible options so that a complex SLA can be constructed.

Support for complex SLA construction may strengthen the solution proposition.

**8.1.12 API Call Logging, Monitoring and Alerts (REQUIRED)**

The ability to implement logging and monitoring of API calls with reporting and administrative alerts. Typically extensive functionality with multiple logging levels is implemented.

Support for flexible levels of logging (for example debug, trace etc.) may strengthen the solution proposition.

**8.1.13 API Call Analytics (RECOMMENDED)**

The ability to implement advanced analytics with out-of-the-box charts and reporting on demand along with the ability to trigger alerts based on analytics.

The strength, flexibility, feature set and appeal of the analytics and charting capabilities may strengthen the solution proposition. Note that this can optionally be implemented as a separate tooling layer perhaps using tools such as Prometheus and Grafana etc.

**8.1.14 API Virtualization (RECOMMENDED)**

The ability to implement virtualized API endpoints. API virtualization is the process of using a tool that creates a virtual copy of your API, which mirrors all of the specifications of your production API, and using this virtual copy in place of your production API for testing.

Note that this is NOT API mocking but provides an actual endpoint for solution testing to proceed unhindered.

**8.1.15 API Developer Portal (RECOMMENDED)**

The ability to publish API specifications through a developer portal using open standards. Includes features such as portal availability across deployment types (on-premise, cloud, etc.), interactive API documentation, developer metrics, developer portal templates, portal customization (HTML, CSS etc.), ability to withdraw developer keys, either temporarily or permanently.

Note that advanced developer portal features may strengthen the value of the solution proposition.

**8.1.16 Flexibility in API Deployment Architectures (REQUIRED)**

The ability to support a diverse array of deployment architectures including standalone, on-premise cloud and public cloud models including the ability to support a fully integrated microservices architecture based on containers. The architecture should also allow for the separation of key components and interfaces for meeting complex network security needs.

Note that the more flexible the deployment architectures are, the stronger the solution proposition.

**8.1.17 Advanced DevOps Artifact Deployment (RECOMMENDED)**

The ability to support advanced DevOps deployment techniques such as “canary deployment”, “blue-green deployment” and “AB testing”.

Additional advanced deployment scenarios and innovations will strengthen the value proposition of the proposed solution.

**8.1.18 File Storage Integration (RECOMMENDED)**

The ability to implement file storage platform integration such as S3 etc. - not exhaustive.

Note that flexibility in the support for storage integration across additional file storage standards will strengthen the value of the solution proposition.

**8.1.19 API Monetization (OPTIONAL)**

The ability to monetize API calls by specific 3rd parties or partners for the purposes of simply raising capital or creating partnership incentives through 3rd party portals. Features such as billing support, support for multiple models of revenue generation, low- to no-code monetization configuration, third-party payment system integration, prepay and/or postpay invoicing, multi-currency support and tax compliance are negotiable.

Note that the more advanced the monetization features are, the higher the solution value proposition is.

**8.1.20 High Availability (REQUIRED)**

The solution provided and any associated components MUST be highly available and utilize clustering technology in order to provide a minimum of 24x7x365 service with 99.99% availability (AKA 4 9’s).

**8.1.21 Open Source Based (RECOMMENDED)**

The offered solution MUST be based fully on open source components. The vendor may offer subscriptions for support so long as the offered solution does not require those subscriptions in order to deliver the core functionality specified in this document.

## 8.2. Identity and Access Management (IAM) Suite Functional Requirements

**8.2.1 Identity Lifecycle Management**

The following diagram defines the basic lifecycle required for managing identities:

<img src="https://lh6.googleusercontent.com/2ePf3F6ttLAbTQjPHDNA3HZnLJU1seMFcZtP8M-y5XrAgwCIzZDXDtAkZhBtCOscV4PuJM8tD1i7LF4AOYcSW-I1tWPvYoWQjHqBaQ5ERLStIPuhsOiRaS7K4ZHxxU72QGeUvEfI" alt="" data-size="original">

What is required is a flexible and comprehensive user lifecycle management solution which provides the following generalized features and functions:

**8.2.1 User Administration Tools (REQUIRED)**

These are required so that administrative users and/or help desk users can centrally manage all user profiles and records. These features include:

* Unlock accounts and reset passwords when needed
* Changing the user status
* Session management – visibility to see active users and to kill their session if needed
* Workflow - monitor all workflows and terminate them if necessary
* Review audit logs for authentication, access and changes to identity records.
* Manage user profile attributes including credentials etc.
* Manage user access rights for resources such as documents and APIs.

**8.2.2 Multi-Source Identity Integration (REQUIRED)**

Integration with multiple source identity systems (such as the Identity BB, databases and LDAP) to automatically initiate provisioning/deprovisioning activities related to enrollment, policy changes and un-enrollment processes.

**8.2.3 Multi-Source Identity Synchronization (REQUIRED)**

Multi-source synchronization of user identity data. This allows the system to integrate and synchronize with an authoritative source such as the national ID, social security system or perhaps more likely the Identity BB via an API/plugin approach. This is required for both initial load of identities and for ongoing provisioning, re-provisioning and deprovisioning etc..

The synchronization must determine which systems a user should be provisioned to/de-provisioned from, which permissions should be set or revoked for the applications that a person is entitled to and whether or not provisioning should be automatic or if an additional workflow should be triggered for human or other automated processing.

**8.2.4 Identity Reconciliation (REQUIRED)**

Automatic user identity record reconciliation. This is where synchronization is used to detect changes in the source system identity data and reconciliation is used to detect, compare and resolve the changes.

For example a user record has been added to a target system manually instead of using IAM.In this case reconciliation can be configured to either:

1. Add the user to the IAM system
2. Remove the user from the target system or;
3. Do nothing but flag the anomaly to an administrator

**8.2.5 Self Service Portal and Workflow (REQUIRED)**

A customizable, workflow driven, self-service user interface portal to enable administrators to create and manage policies, users and the various artefacts. Must support approval workflows to multiple stakeholders.

**8.2.6 Advanced Password Management (REQUIRED)**

The advanced password management capabilities must include the following:

* Self-service Password Reset (SSPR)
* Administrative change password
* Password synchronization with directory and other resources.
* Must work across both cloud and on-premise applications lowered costs and improved security for hybrid cloud deployments
* Ability to enforce strong password policies
* Self-service password which allows users to reset their own password without going to the help desk. Reset is via a combination of challenge/response questions, one-time link via registered email, one-time token via SMS or mobile device messaging and one-time PIN.
* Password aging with password change reminders sent via email and potentially mobile messaging.
* Password change synchronization across all target systems.

**8.2.7 User Access Request Management (REQUIRED)**

Whilst provisioning processes can be triggered through the automated user lifecycle management functionality, the IAM solution must also provide a self-service feature through the portal via which end-users can request access. This access-request functionality is provided through a shopping cart and service catalog design where the user has access to select the services to which they would like to request access. Applications and application-specific entitlements such as membership to an LDAP group or a role on a public cloud provider such as AWS must be supported as a part of the access grant process.

The access request feature must also include the optional selection of a “Profile Role” capability – which is a role defined for a job/position that can grant access to a number of applications that are needed for a particular job role (otherwise known as delegation).

The access request/approval workflows provided must support:

* Multiple approvers – Must be able to define as many approval steps needed and select common targets such as a supervisor, object owner or admin, and group of approvers.
* Service Level Agreements (SLA) - Must ensure that tasks are completed in a timely manner so if they are not, then they can be escalated to the appropriate person after expiry time.

The access request approval functionality must also support basic “delegated approval” and “out of office” functionality so that there are no barriers to self service access requests when the usual approvers are not available.

**8.2.8 REST API (REQUIRED)**

A REST (representational state transfer) based API for external integration of the provisioning and deprovisioning of users etc.. is required. It must support the same OpenAPI standards defined by the Architecture Blueprint and Functional Requirements (see Ref 1). An example of such a REST API is provided with the OpenIAM suite specification here: [https://www.openiam.com/products/identity-governance/features/api/](https://www.openiam.com/products/identity-governance/features/api/). This is intended as an example of the API style that is expected in such a suite. This is not definitive and may vary based on the proposed IAM suite.

**8.2.9 Orphan Management (REQUIRED)**

Organizations which are not actively using an IAM platform often have orphaned user records in their business applications. These are those records which are the result of users being given access and not having that access revoked when a person is unenrolled from a service.

Orphan management functionality consolidates all the orphaned records and provides administrators with tools to either clean up these records or link them to the correct user.

**8.2.10 Access Certification (REQUIRED)**

Regulatory requirements, such as GDPR, HIPPA and SOX combined with an increased focus on security are causing both public and private organizations to implement access certification policies. Scheduled access certification campaigns aid in complying with these regulatory mandates as well as improve security by guarding against the access violations which lead to security breaches.

However, when performed manually, these activities can be error prone and very time consuming for most mid to large organizations. The lack of consistency resulting from manual processes results in failed compliance audits and threats resulting from unauthorized access can slip undetected. The IAM solution must provide the ability to automate the access certification process which addresses the challenges found when performing these processes manually.

The following types of certifications must be supported by the IAM solution:

* User Access Certification
* Application Access Certification
* Group Access Certification

These campaigns can be scheduled and run at regular intervals or they can be run on demand. The Access Certification functionality in the IAM solution must provide organizations with the following capabilities:

* Human Friendly Reviews: End-users (reviewers) using the IAM solution access certification functionality must be able to perform their activities in a familiar self-service user interface. Reviewers must be able to review all the historical access in a central location as well as use tools to compare access (date, time, service etc.) between individuals.
* Closed Loop Revocations: During the certification process, reviewers must be able to revoke accounts and entitlements with a simple one-click mechanism. The closed-loop validation mechanism will then ensure that revoked access has been deprovisioned from the target applications.
* Support for Cloud, On-Premise and Hybrid Cloud: An increasing number of organizations today have hybrid environments where applications are deployed both on-premise and in the cloud. The IAM solution must provide a central identity governance platform such that the same consistent certification programs can be undertaken irrespective of the applications and infrastructure location.
* Enrollment (Joiner)
* Role Change (Mover, Additional Services)
* Unenrollment (Leaver)
* Status change
* Access request (Additional Services)
* Group creation (with group policy)
* Self-registration (with a customized external workflow to integrate with the Identity BB)
* Access Certification

The following predefined workflow templates are required to be provided:

* Multiple approvers
* Service Level Agreements (SLAs) to ensure timely completion (with automatic delegation and temporary changes in the new approvers access rights to enable time-sensitive approval)

Each of these workflows must support:

The IAM solution identity governance feature set must provide the creation of workflows to support complex processing, integration and approval steps. While custom workflows must be defined, the IAM solution must also provide default out-of-the-box workflow templates for common operations to simplify the configuration effort.

**8.2.11 Workflow Creation (REQUIRED)**

The IAM solution identity governance feature set must provide the creation of workflows to support complex processing, integration and approval steps. While custom workflows must be defined, the IAM solution must also provide default out-of-the-box workflow templates for common operations to simplify the configuration effort.

Each of these workflows must support:

* Multiple approvers
* Service Level Agreements (SLAs) to ensure timely completion (with automatic delegation and temporary changes in the new approvers access rights to enable time-sensitive approval)

The following predefined workflow templates are required to be provided:

* Enrollment (Joiner)
* Role Change (Mover, Additional Services)
* Unenrollment (Leaver)
* Status change
* Access request (Additional Services)
* Group creation (with group policy)
* Self-registration (with a customized external workflow to integrate with the Identity BB)
* Access Certification

**8.2.12 Custom Workflows (RECOMMENDED)**

Whilst the IAM solution must provide the above workflow templates, it also must include a BPMN compliant workflow engine that can be used to create new custom workflows. A graphical process designer such as the BPMN designer plugin such as one of the many available for the Eclipse IDE or similar must be included to simplify the effort required to create new custom workflows.

**8.2.13 Audit and Compliance (REQUIRED)**

Facilitating compliance with regulatory requirements or internal security policies is one of the principal drivers for Identity Governance. The IAM solution must provide tools to help organizations meet compliance mandates.

Organizations deploying the IAM solution as a part of GovStack are required to automate a variety of operations that sometimes utilize workflow-based approval steps.

Detailed audit logs must be associated with each of these operations so that organizations can answer the following fundamental questions:

* What access rights does a user currently have?
* When were they granted these rights?
* How or why were they granted these rights and by whom were they granted?

In addition to access information, the IAM audit logs must also track details related to authentications, password changes, life cycle status changes, system configuration changes etc.. Using the information provided by these logs, combined with the out of the box reports, and self-service tools, organizations must be able to achieve the following:

* Provide the auditors with clear evidence of compliance or otherwise.
* The ability to proactively review, detect and revoke inappropriate access from any user.
* The ability to review all access rights before granting any additional access rights.
* A centralized review and certification of applications/systems access rights across both on-premise and cloud.

**8.2.14 Connectors (RECOMMENDED)**

The IAM solution should provide a large range of connectors for both source and target applications out-of-the-box, The reason for this is that GovStack will be deployed in more than one country and in unknown applications environments and must be able to be integrated with many different common enterprise information systems and services both on premise and in the cloud in a simple and cost effective manner… for example:

* Microsoft (Active Directory, PowerShell, Windows, Azure AD, Exchange, SQL Server, Office 365, Azure DevOps, Dynamics365)
* Oracle (eBusiness Suite (EBS), IDCS, database)
* ERP/HR Systems (Oracle, SAP, ADP, Workday)
* Public Cloud (Amazon Web Services, Azure, Google Cloud)
* Infrastructure (Database/JDBC, GIT, LDAP (OpenLDAP, eDirectory, Active Directory, ApacheDS etc.), Linux (RHEL, CentOS, Ubuntu), REST web services, SCIM 2, scripts)
* Others (Google Gsuite, Salesforce, SAP Hana, Slack (SCIM), Tableau… not an exhaustive list)

**8.2.15 Access Management (REQUIRED)**

Access management is an integral part of the required IAM solution. The Access Manager must provide a scalable, secure and consistent solution to implement policy based access for applications in hybrid cloud environments for both internal (employees), citizens (external) and 3rd parties (external) alike.

The Access Manager must provide the following tools to enable these objectives:

* **Web SSO.** Web single-sign-on must be provided with support for SAML 2, oAuth 2, OpenIDConnect, OIDC, and a proxy to allow SSO to legacy applications. This enables web based applications to be easily configured for SSO without modification.
* **Adaptive Authentication.** An adaptive authentication system as follows must be provided with the following features:
  * Password-based authentication
  * Certificate-based authentication
  * MFA-SMS/E-mail/Mobile app-based OTP
  * Adaptive Authentication builds on these options to provide a robust framework where users can build rich authentication workflows using a browser-based drag-and-drop interface.
  * The flows can take into account a broad range of risk factors including device, context, user choices, geolocation, profile attributes, user behavior and foundational identity systems.
  * This allows the implementation of a solution which offers a significantly higher level of security while providing an improved end-user experience in comparison to traditional options.
* **Multi Factor Authentication (MFA).** While the IAM solution framework must allow the use of third party MFA products, it should also provide its own MFA solution which is pre-integrated and ready to use. The following MFA options should be provided out-of-the-box:
  * SMS-based OTP
  * E-mail-based OTP
  * Mobile app (iOS or Android) OTP plus push notification support
* **Social Sign-on (as opposed to single-sign-on).** The Access Manager should allow social sign-on from social identity providers such as Google, Facebook and LinkedIn. Social registration significantly reduces the registration effort by allowing select attributes to be dynamically transferred from the social provider. This may or may not be used in practice but is a desired feature.

**8.2.16 RBAC Based Authorization (REQUIRED)**

The IAM solution must provide a flexible RBAC-based authorization model to enforce security into applications through the Access Manager. The RBAC model must support inheritance as well as direct entitlements and provide the flexibility needed to implement complex real world requirements. The authorization service must be able to be used in conjunction with oAuth2 and the Access Gateway to enforce the authorization rules.

**8.2.17 Session Management (REQUIRED)**

The IAM solution must provide session management for issues like session timeout to reduce the exposure created by long running sessions. This includes API’s to extend expiring tokens etc. for application and user convenience.

**8.2.18 Device Registration (REQUIRED)**

The IAM solution must provide device registration such that only registered devices can be used to access services by policy.

**8.2.19 Fine Grained Audit Logging (REQUIRED)**

The IAM solution must provide fine grained audit logging by the Access Manager so that the explicit date, time, user and service access is logged.

**8.2.20 Access Gateway (REQUIRED)**

An access gateway is required in order to provide protected proxy gateway access to the web through reverse and front side web infrastructures such as Apache and Nginx web servers. This must provide the following functionality:

* SSO to legacy applications
* Session management
* Protection of APIs and application URLs by enforcing authentication and authorization rules unless a 3rd party API Management and Gateway suite is used in which case the access gateway must be configurable to utilize the 3rd party API Gateway.

**8.2.21 Legacy SOA Security Features (REQUIRED)**

The IAM suite should be able to implement a pure legacy SOA approach. A legacy SOA API with all required operations should be available to facilitate integrations with legacy SOAP/SOA systems. The IAM solution should provide SOA federation for controlling access to services in a legacy SOA environment using SAML, SAML 2 and WS-Security. The IAM solution must be able to enforce policies throughout SOA based services. RBAC and XACML support must be provided to allow the IAM solution to implement a flexible security model that supports the following:

* Distributed services (vs monolithic applications)
* Services distributed across organizational boundaries
* Service Interoperability
* Integration of disparate legacy SOA protocols

**8.2.22 Web Access Management (REQUIRED)**

The Access Gateway must be able to provide coarse-grained authorization when protecting web applications in totality. Requests must be routed through a proxy, which applies authorization rules, and forwards the request to the underlying servers, providing the application.

The model must be simple to deploy and easy to maintain. User identity must be checked and propagated through HTML header injections, HTTP query strings or HTTPS authentication headers to applications hidden behind a proxy server for the purposes of openness and compatibility. The native URL of these applications must be hidden from the public view (i.e. it is only exposed as a service name in a secure manner).

**8.2.23 Single Sign On (SSO) (REQUIRED)**

Each partner application, as well as internal applications and building blocks, may have their own set of security credentials and various authentication methods. Such applications may move in and out of security domains.

The user experience suffers when many login credentials must be remembered. Therefore the IAM solution must provide SSO features that allow users login once and roam unchallenged through a security realm to which they have been granted access.

This reduces the burden of many passwords and eliminates the need to individually login to each application. Users must be able to login once, and roam freely across secured domains without being challenged again. Participating security domains must never be required to give up their own credentials.

The ability to hold multiple identities, each with their own roles, permissions, access-levels and entitlements across multiple domains is required and allows for a wide network of co-operating domains to communicate seamlessly.

Authenticated subjects must be able to access restricted resources requiring multiple logins and credentials without the need to login at each domain. The IAM solutions access manager solution must not be based on a proprietary cookie. It should be based on SAML 2, which is a well-accepted industry standard for SSO.

Using SAML2 allows the IAM solutions access manager to not only provide SSO capability at the web application tier, but also across other layers such as Web Services in a completely unified way. SSO must also allow the access manager to integrate easily with existing authentication technologies that are deployed in any organization.

**8.2.24 Federation (REQUIRED)**

When GovStack is deployed it will need to be deployed with partners, suppliers and other organizations. For them to collaborate effectively, identity information needs to be propagated. The IAM solution must be able to manage the processes for federating users when a partner site comes on board or leaves. Federation capabilities must be provided by the IAM access manager solution. New cost recovery streams may be generated for GovStack users through enablement of trusted partnerships where authentication and authorization is carried out over federated business networks.

Federation refers to interoperation between entities in different security domains, either in different organizations, or in different tiers in the same organization.

A trust relationship must exist between the involved entities to federate identity and enable authentication across realms. Each domain may rely on different technologies and mechanisms to authenticate and authorize.

Federation enables loose coupling at the IDM level separating the way each organization/application/module/building block does its own security implementation while they adopt a common mechanism to propagate identity.

**8.2.25 Security Token Service (STS) (REQUIRED)**

STS is a system role defined by the WS-Trust specification. A Web Service Client interacts with the STS to request a security token for use in SOAP messages. In addition, a Web Service Provider interacts with an STS to validate security tokens that arrive in a SOAP message. An STS arbitrates between different security token formats.

The token transformation capability defined in WS-Trust provides a standards-based solution to bridge incompatible federation deployments or web services applications. Web service providers should not be required to support multiple authentication mechanisms even though they have to work with different web service clients.

The SAML standard is well recognized and the IAM solution must provide a Security Token Service that can validate SAML and SAML2 tokens to bridge different web services.

**8.2.26 Role and Attribute Based Access Control (RBAC/ABAC) (REQUIRED)**

The IAM solutions Access Manager must manage Groups, Roles, Permissions and Resources supporting both RBAC and ABAC. Groups are generally used to model organizational structure whereas Roles are used to model a person’s function within the enterprise. In RBAC, a subject is given one or more roles depending on the subject’s job.

Access is determined by the subject’s role. In ABAC (Attribute Based Access Control), access is determined by the attributes of the subject (person or entity), attributes of the resource being accessed, environmental attributes and the desired action attribute. ABAC is implemented based on the XACML specification with:

* Coarse-grained access control - based on subject, role and permissions
* Ease of administration - roles created for job functions
* A subject that must be assigned to a role and execute actions that are authorized for the role
* Assigned permissions for job functions based on operations rather than to resource objects
* Enablement of the creation of:
  * Relationships between Users, Groups, Roles, Resources
  * Creation and enforcement of policies

Developing an access control strategy based on RBAC provides a clean and flexible model that is easy to maintain over a long period of time.

Policies may be associated with a person’s role. For example, someone in a medical advisor role may be permitted to access applications pertinent to his or her role, but not permitted to access applications related to someone in a doctor's role.

## 8.3 Service APIs

This section describes external APIs that must be implemented by the building block. Additional APIs may be implemented by the building block (all APIs must adhere to the standards and protocols defined), but the listed APIs define a minimal set that must be provided by any implementation.

All APIs will be defined using the OpenAPI (Swagger) standard. The API definitions will be hosted outside of this document. This section may provide a brief description of required APIs. This section will primarily contain links to the GitHub repository for OpenAPI definition (yaml) files as well as to a website hosted by GovStack that provides a live API documentation portal. The basic assumption here is that the IAM suite will be acquired and not built. The suite MUST supply an appropriate API with documented endpoints.

IAM Suite API: An example of such a REST API is provided with the OpenIAM suite specification here: [https://www.openiam.com/products/identity-governance/features/api/](https://www.openiam.com/products/identity-governance/features/api/). This is intended as an example of the API style that is expected in such a suite. This is not definitive and may vary based on the proposed IAM suite. The detailed API documentation for OpenIAM including interface specifications can be found here: [https://docs.openiam.com/docs-4.1.14/html/API/index.htm](https://docs.openiam.com/docs-4.1.14/html/API/index.htm)

OAuth2 API: The following link describes how OAuth2 is used in OpenAPI 3.0 standards based identity and access: [https://swagger.io/docs/specification/authentication/oauth2/](https://swagger.io/docs/specification/authentication/oauth2/).

SCEP API: A description of the OpenXPKI enrollment workflow and API can be found here: [https://openxpki.readthedocs.io/en/latest/reference/configuration/workflows/enroll.html](https://openxpki.readthedocs.io/en/latest/reference/configuration/workflows/enroll.html). This is an example of how an API for enrolment with its associated workflow should be implemented within the Certificate Authority Server.

LDAP API: A description of the standard REST LDAP API provided by the open source 389 Directory Server here: [https://directory.fedoraproject.org/docs/389ds/design/ldap-rest-api.html#ldap-rest-api](https://directory.fedoraproject.org/docs/389ds/design/ldap-rest-api.html#ldap-rest-api) . This is an example of how an open API for credential storage and retrieval using LDAP should be implemented.

## 8.4 Workflows

A workflow provides a detailed view of how this building block will interact with other building blocks to support common use cases.

This section lists workflows that this building block must support. Other workflows may be implemented in addition to those listed.

No specific workflow definitions are required for this building block as they will be inherited by the tools/products chosen to address each security issue/concern and fundamentally deal with the other building blocks API’s in a cross-cutting manner as in the case of API Management.

Other components of the Security BB such as the IAM Suite will also provide their own workflow tools but the details of the actual workflow need to be designed once more is known. An example of the type of default workflow provided for an IAM suite would be the basic workflow for provisioning new accounts which can be leveraged by the other BBs. This is typically a basic workflow built in a tool that can be customized to meet specific provisioning needs (perhaps with multiple administrative roles and connections to multiple external systems and modules etc.) . The following link describes an example the basic workflow for provisioning provided by Open IAM (one of the alternatives) [https://www.openiam.com/products/identity-governance/features/provisioning/](https://www.openiam.com/products/identity-governance/features/provisioning/)

Note that each building block is responsible for the defining base configurations and workflows required to be created in the IAM system that enable identity and access to be provisioned. Essentially the IAM system needs to be augmented with adapters to enable identity and access to be provisioned to target systems and resources in the way that the target applications implement their own identity and access. Alternatively where applications are built from the ground up they can leverage the IAM suite sAPI services to implement authentication and access.

These specific workflows and adapters can be defined at the detailed design stage and communicated to the Security WG for implementation in the IAM solution. It must be noted that the security WG is NOT responsible for determining the identity and access policy and the details of access for each role for example. The following need to be identified by each building block and communicated to the Security WG for implementation in the IAM suite configuration build:

* Resource Types: for example files, services, API’s, applications, modules to be protected by IAM.
* Resources: The definitions of the actual resources and their type provided by and required by each BB that are to be secured through IAM. This must include the target system or component that hosts these resources so that the correct provisioning adapter can be configured for that resource. Note that where the BB or resource has its own identity and access scheme an adapter can be written using the IAM suite API.
* Roles: the roles of users of each system that include the required resource access for that role in terms of the Resources. Each BB must account for the access they require to be provisioned to other services as a part of their process scope. In the case of provisioning a new account there is a need for a broader workflow process that is outside the scope of the Security BB which incorporates the Identity and Registration BB. For example a Doctor role may require verification and validation of certain aspects of identity prior to provisioning access to a specific service. A basic set of sequence diagrams is provided below to reinforce the understanding of what is required.
* Approval Workflows: workflow for the approval of the various identity and access requests (complete with approval roles etc).

### 8.4.1 Identity and Access Sequences

The following sequence diagrams depict the basic means by which authentication and access control shall be implemented across building blocks. Note that by definition an account with no access can be created by any user. via self-registration. Self-registration using basic phone/email as well as strong self registration using foundational ID are to be supported . A sequence detailing technical authentication is also included below along with sequences defining the remaining aspects of the identity lifecycle (such as provisioning and deprovisioning of access) to be supported by the IAM suite and how they will be leveraged by all building blocks. Such workflows can be articulated in full during the detailed design phase:

#### **8.4.1.1 User authentication and authorization**

![See https://www.websequencediagrams.com/  for an editable diagram](../@site/static/img/www.websequencediagrams.com.png)

This assumes the user already has an account. Authentication credentials are username or phone number and password.

The auth token could be signed with an expiration (JWT) which might allow the BB to perform the validation themselves. Additionally, if the token contains roles and/or a user ID and isn’t expired the BB could potentially rely on those.

#### **8.4.1.2 Self-registration via phone number or email**

![See https://www.websequencediagrams.com/  for an editable diagram](<../@site/static/img/www.websequencediagrams.com (1).png>)

#### **8.4.1.3 Self-registration via foundational ID**

For a specification, see the [Identity and Verification Building Block Specification](broken-reference/).

Note that role creation (e.g. farmers, doctors) is handled by the IAM solution, via either an administration UI or an API. Building blocks can create roles via the API to provision new roles.

It’s assumed the user clicked a link to access the service in the Building block UI.

The users are authorized with a valid access token for their email or phone number.

#### **8.4.1.4 Self-deprovisioning via foundational ID**

![See https://www.websequencediagrams.com/  for an editable diagram](<../@site/static/img/www.websequencediagrams.com (4).png>)

This flow assumes the user has an account and is currently authenticated.

#### **8.4.1.5 Deprovisioning via government official**

![See https://www.websequencediagrams.com/  for an editable diagram](<../@site/static/img/www.websequencediagrams.com (3).png>)

This flow assumes the user has an account and is currently authenticated.

#### 8.4.2 Standards

The workflows MUST adhere to all standards defined in this document as well as in the GovStack architecture document (link to appropriate section in architecture document)

**No specific standard workflows are required in the context of the security building block. All workflows involving identity and access for example are the responsibility of each building block working group and to be defined during detailed design. Such workflows can and should be implemented using the workflow engine built into the IAM suite and perhaps extended from or to a meta-workflow defined in the context of another BB.**

#### 8.4.3 Interaction with Other Building Blocks

The security building block predominantly deals with the cross-cutting security concerns of each other building block and defines the basis for the implementation of solutions to address these concerns. The only interaction required is for API Management and Gateway services. These interactions are depicted and documented in Architecture Blueprint and Functional Requirements (see Ref 1).

#### 8.4.4 Example Sequence Diagrams for API Gateway Services

The sequence diagrams below depict examples of how a building block might interact with the API Management and Gateway solution. This is only relevant for the API Management and Gateway services in the context of the security building block. A higher level sequence diagram depicting API interactions for building blocks is depicted and documented in Architecture Blueprint and Functional Requirements (see Ref 1).

![Example Sequence for Issuing a Token for API Access](../@site/static/img/image8.png)

![Example Sequence for Calling an API Microservice via Gatewa](<../@site/static/img/image7 (3).png>)
