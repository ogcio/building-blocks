# 2 Introduction

This document is intended to provide guidance for building block working groups and developers of products that will be integrated into a GovStack implementation. It also provides guidlines for implementers and system integrators who are deploying solutions that leverage the GovStack approach. It provides guidelines and principles that should be considered by all building blocks and cross-cutting requirements that must be considered for any GovStack project.

This will accelerate the collaborative development of best-of-breed digital public goods, enhancing efficiency and transparency across the world - especially in low-resource settings.

## 2.1 GovStack and the Building Blocks Approach

GovStack aims to provide a reference architecture for digital governance software to support sustainable development goals. Rooted in a "Whole-of-Government" approach, the GovStack Framework provides a methodology for leveraging common technology components and infrastructure to more easily create and deploy interoperable digital platforms which can address high-priority use cases across multiple sectors. The guidelines and requirements described in this document provide a framework for the development of digital building blocks oriented toward this goal.

## 2.2 Criteria for Building Blocks

The following provide criteria and definitions for Building Blocks, developed by organizations whose work is focused around achievement of the Sustainable Development Goals (SDGs). The criteria are drawn from the [SDG Digital Investment Framework](https://dial.global/research/sdg-digital-investment-framework/), developed by the International Telecommunication Union (ITU) and the Digital Impact Alliance (DIAL), as well as the [definition of Building Blocks](https://digitalpublicgoods.net/DPI-DPG-BB-Definitions.pdf) developed by the Digital Public Goods Alliance (DPGA):

### A Building Block:

* Refers to software code, platforms, and applications that are interoperable, provide a basic digital service at scale, and can be reused for multiple use cases and contexts.
* Serves as a component of a larger system or stack.
* Can be used to facilitate the delivery of digital public services via functions, which may include registration, scheduling, ID authentication, payment, data administration, and messaging.
* Building blocks can be combined and adapted to be included as part of a stack of technologies to form a country’s Digital Public Infrastructure (DPI).
* Building blocks may be open source or proprietary and therefore are not always DPGs.

"Building blocks can be as simple as a common set of rules or protocols (for example email programs like Simple Mail Transfer Protocol - SMTP), or complex (for example an open-source health information system like the DPG, District Health Information Software - DHIS2)“

Characteristics of building blocks:

* Autonomous: building blocks provide a standalone, reusable service or set of services, they may be composed of many modules/microservices.
* Generic: building blocks are flexible across use cases and sectors.
* Interoperable: building blocks must be able to combine, connect, and interact with other building blocks.
* Iterative evolvability: building blocks can be improved even while being used as part of solutions.

Per the DPGA definition, to be considered a building block, solutions must meet the following technical requirements determined by the GovStack Initiative which includes:

1. Open API, Open API Specifications, Rest API
2. Packaged in a container
3. Include a information mediator where communication flows between services that are not co-located

## 2.3 Building Block Layers

Building blocks are software modules that can be deployed and combined in a standardized manner. Each building block is capable of working independently, but they can be combined to do much more:

<figure><img src="../@site/static/img/31.-A-common-reusable-stack-of-Building-Blocks_2 (1).jpg" alt=""><figcaption></figcaption></figure>

Building blocks are composable, interoperable software modules that can be used across a variety of use cases. They are standards-based, open source and designed for scale.

Each Building Block represents, as much as possible, the minimum required functionality (MVP) to do its job. This ensures each Building Block is usable and useful on its own, and easily extensible to support a variety of use cases.

A Building Block is composed of domain-driven microservices, modeled as closely as possible on existing roles and processes. This helps ensure each building block is as useful as possible in the real world.

Building Blocks exchange data using lightweight, human-readable data that can easily be extended where needed. Data models and APIs are described in a lightweight manner that’s human-readable, allowing them to be easily and quickly understood and validated.

![](<../@site/static/img/image3 (2).png>)

## 2.4 Cross-Building Block Communication

A building block is only so useful on its own. In practice, building blocks MUST be connected together in a secure, robust, trusted manner that facilitates distributed deployments and communications with existing services.

It is STRONGLY RECOMMENDED that a building block uses an information mediator (as described below and in the [Information Mediator Building Block specification](https://govstack.gitbook.io/bb-information-mediation)) for any communications across the internet. An Information Mediator is not required for communication between building blocks which are co-located. In this case, communication may occur using standard API calls.

### 2.4.1 Federation and Data Exchange Requirements

Each building block deployment SHOULD use an Information Mediator to federate and communicate with other data consumers and providers, particularly when communicating between services that are not co-located. This ensures the confidentiality, integrity, and interoperability between data exchange parties. An Information Mediator MUST provide the following capabilities:

* address management
* message routing
* access rights management
* organization-level authentication
* machine-level authentication
* transport-level encryption
* time-stamping
* digital signature of messages
* logging
* error handling
* monitoring and alerting
* service registry and discovery

Refer to the full description of the [Information Mediator Building Block ](https://govstack.gitbook.io/bb-information-mediation)for more information.

### 2.4.2 Organizational Model

In order to effectively deploy a software solution using the Information Mediator, several policies and processes will need to be applied. This section briefly describes that organizational processes that must be in place.

First, a central operator will be identified and created. This organization will be responsible for the overall operation of the system, including operations and onboarding new members. Policies and contractual agreements for onboarding need to be created.

Next, trust services need to be set up internally or procured from third parties, including timestamp and certificate authorities. This provides the necessary infrastructure to support distributed deployments.

Finally, members can be onboarded and provided with access to the Information Mediator and methods to register the services that they provide as well as discover services that are available.

Once agreements are in place, members can deploy new services in a decentralized, distributed manner. Before deploying a new service, the central operator must be notified of any changes to access-rights, including organization and machine-level authentication before it can publish or consume data.

### 2.4.3 Technical Architecture

This section provides an overview of the technical processes and architecture that must be implemented once the organizational model has been created.

1. A Central Operator is responsible for maintaining a registry of members, the security policies for building blocks and other member instances, a list of trusted certification authorities and a list of trusted time-stamping authorities. The member registry and security policies MUST be exposed to the Information Mediator.
2. Certificate authorities are responsible for issuing and revoking certificates used for securing and ensuring the integrity of federated information systems. Certificate authorities MUST support the Online Certificate Status Protocol (OCSP) so that an Information Mediator can check certificate validity.
3. Time-stamping authorities securely facilitate time stamping of messages. Time stamping authorities MUST support batched time stamping.
4. The Service Registry provides a mechanism for building blocks to register the services that they provide and for other building blocks to discover and consume those services. Any services provided or consumed by a Building Block that leverages the Information Mediator architecture MUST use this service registry functionality.

## 2.5 Keywords and Definitions

Within this document, the key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) [RFC2119](https://tools.ietf.org/html/rfc2119) [RFC8174](https://tools.ietf.org/html/rfc8174) when, and only when, they appear in all capitals, as shown here.

### 2.5.1 Building Block-specific definitions

The following provides definitions for terms that are used by various building blocks.

**Registration:** Any approval/license/certificate issued by a public entity as a result of a request/declaration made by a user of the public service. The result of a “registration” is usually a number and/or a document (called certificate, license, permit, authorization, registration, clearance, approval, etc.)

**Authentication:** This is the technical process of establishing that the credentials (i.e. username, password, biometric etc.) provided by a party (user, system, other) is valid and that the party can be granted basic access to system resources with default access rights. Note that authorization also needs to be applied for a party to access protected resources.

**Authorization:** This is the technical process of establishing whether or not an authenticated party has rights to access a given protected resource. Access rights can typically be granted or revoked administratively on a read-only and/or read-write and/or execute basis through an administrative provisioning process. Permissions or rights defined for a party typically manifest in an access token that is granted at the time of authentication for the party. Hence the processes of authentication and authorization are intrinsically related.

**Workflow Terminology:** See more comprehensive descriptions of the workflow terminology in the [Workflow and Business Process Automation Building Block specification](https://govstack.gitbook.io/specification/building-blocks/workflow).

* (Workflow) Activity - a single step in a workflow process.
* (Workflow) Process - a workflow process contains one or many activities.
* (Workflow) Instance - an instance of execution for a workflow process.
