# 2 Description

The Security Requirements document provides cross-cutting guidance for any GovStack implementation, whether an individual Building Block or a full GovStack solution to address one or more use cases. It provides a reference for security concerns and requirements for how to implement and deploy secure solutions.&#x20;

This document also describes a set of 'Authorization Services' that should be implemented for any GovStack implementation. The authorization services provide secure communication between building blocks as well as a mechanism for user authentication and definition of roles and permissions for users.&#x20;

## 2.1 Cross-Cutting Security Requiremetns

Security requirements address all cross-cutting security issues and concerns for the whole GovStack digital platform including every layer, every building block and all applications. Although other building blocks address “some” security aspects such as “Identity building block” (addressing the foundational identity aspects and document workflows etc.) the resultant solutions delivered by all building-blocks (including the “Identity building block”) MUST comply with the standards and requirements set by this security requirements document. This document covers security requirements of two types:

* **Build-time Security**: These are considerations for embedding security during development of building blocks and applications.
* **Deployment time Security**: These are considerations for enforcing security measures in deployed systems during run-time.

These may consist of cross cutting functionalities that can be utilized for various building blocks and specific requirements for the **Security Building Block itself, to** provide secure internet access for user interaction with applications and building blocks in Govstack.

The security requirements are based on the [NIST CyberSecurity Framework](https://www.nist.gov/cyberframework/getting-started) and defined herein through review of GovStack use cases and best practices for securing and hardening government infrastructure. It MUST also be noted that the security building block defines the core requirements to implement policy based API security and management across the internal building blocks as well as external applications and 3rd party services consumption. This is based on the architectural assumption that all inter-building block communication/integration with external applications and users MUST be through REST APIs.

## 2.2 Authorization Services

Though these security requirements are cross-cutting, this document also provides guidance on how to implement core 'Authorization Services' within a GovStack implementation. These services provide the mechanism for user authentication, tracking the specific permissions and roles that a user has and managing access to the various Building Blocks that are consumed by the application. The functions of the Authorization Services include the following:

* User authentication
* Management of access to Building Block APIs
* API Gateway functionality which will manage incoming requests
* Identity and Access Management and/or Role-Based Access Control.

These modules are described in Sections 7 and 8 of this document (Authorization Services and Additional Security Modules)
