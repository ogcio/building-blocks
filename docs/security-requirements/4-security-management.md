# 4 Security Management

The key security functionalities outlined here describe the required facilities that this security building block MUST provide as well as security compliance measures that must be implemented by all building blocks. Note that specific API definitions are not likely to be created by the security building block as any interfaces required are to be based on open standards and implemented as part and parcel of acquired solutions. A good example of this is the adoption of standards like OAuth2 and OpenIDConnect for authentication and authorization. The functional requirements for the implementation of an appropriate API Management and Gateway services solution can be found in a separate section of this document below.

The basic framework by which security is addressed for GovStack is largely based on the [NIST CyberSecurity Framework](https://www.nist.gov/cyberframework) (hitherto referred to as NIST CSF) and the [NIST 800-171 Rev.2](https://csrc.nist.gov/publications/detail/sp/800-171/rev-2/final) standard (hitherto referred to as NIST 800-171) for managing controlled unclassified information (CUI) but does also incorporate other security related requirements. The GovStack security requirements are also informed by and should be compatible with the [ISO/IEC-27001:2022 Information security, cybersecurity and privacy protection requirements](https://www.iso.org/obp/ui/#iso:std:iso-iec:27001:ed-3:v1:en) (hitherto referred to as ISO-27001).

The Specific GovStack Security Related Concerns is organized in terms of the major functions of the NIST CSF which is defined by NIST as 3 major approaches/facets for implementation:

## 4.1 Specific GovStack Security Related Issues

This section of the document provides a specific list of the concerns, principles, procedures and actions (collectively termed as security related issues) that have been identified for GovStack along with:

* How each issue maps to the existing building blocks and their respective working groups
* What type of organizational risk is anticipated if the issue is not addressed (i.e. high/medium/low)
* Which target phase of the project the issue must be addressed in (i.e. first/second) - third phases are usually never completed
* How feasible it is to address the issue in a limited-resource or low-resource setting (predominantly related to costs) - see the [Architecture Blueprint and Non-Functional Requirements](../architecture-and-nonfunctional-requirements/) document for the definitions associated with low-resource settings.

A general description and/or discussion of the issue that needs to be addressed and the various alternatives available for addressing it (not exhaustive). The security issues are organized by the 5 NIST functions (Identify, Protect, Detect, Respond, Recover).

## 4.2 Security Issues by NIST Function

### 4.2.1 IDENTIFY

#### 4.2.1.1 Authentication and Authorization

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity\
**Description:** Authentication and Authorization MUST be addressed across the board. It is likely to be built-in to API Management and Gateway and accessed by mobile and web applications using a token based approach. All communications from all clients (web/mobile/BB clients etc.) MUST be via API so this is a sensible point of implementation given the stateless nature of applications. Authentication and authorization MUST also be addressed at an application access level for each and every application (web/mobile/desktop etc). It would be wise to utilize the same framework and capabilities for this.\
**Comments:** Each building block MUST implement centralized authentication and authorization (minimally proxied or implemented via the common IAM solution and/or API Management and Gateway services).

#### 4.2.1.2 Multi-Factor Token and Password Strength/Complexity Management&#x20;

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Credential strength management is likely built-in to API Management and Gateway. All communications from all clients (web/mobile etc.) must be via API so this is a sensible point of implementation also. Each application MUST provide the ability to determine credential strength at the time of registration and thus permit or deny the offered credential.\
**Comments:** Each building block MUST implement Multi-Factor Token and Password Strength/Complexity Management for an indeterminate array of factors including biometric (this is to be implemented through leveraging a common IAM solution).

#### 4.2.1.3 Access Control (RBAC, MAC, DAC)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Access control is also likely built-in to API Management and Gateway. All communications from all clients (web/mobile etc.) must be via API. The thin client nature of web and mobile dictates that all resources will exist behind API interfaces so this is the most sensible point to address it (i.e. either they have access to the API or they do not).\
**Comments:** Each building block MUST implement role based access control for all exposed API’s and resources (minimally proxied or implemented via the API Management and Gateway services)

#### 4.2.1.4 Provisioning, Deprovisioning and Management of Identities and access rights

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Will need a process based solution for this. This selection will largely depend on the identity management and API management infrastructure chosen but will likely need to be a customized process that integrates provisioning across a number of products and services.\
**Comments:** Each building block MUST implement the ability to provision, deprovision and manage Identities and access rights (this may or may not be centralized for the whole architecture as a unified provisioning process).

#### 4.2.1.5 Access and Authorization Audit, Logging, Tracing, Tracking

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Likely built-in to API Management and Gateway. All communications from all clients (web/mobile etc. must be via API)\
**Comments:** Each building block MUST implement access and authorization audit, logging, tracing and tracking with alerts (minimally proxied or implemented through the API Management and Gateway services).

#### 4.2.1.6 End User Device Registration, Deregistration, Re Registration and Device Platform Security

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Significant functionality provided by MOSIP - TBD\
**Comments:** Each building block dealing with physical devices MUST implement end user device registration, deregistration, re-registration and device platform security guidance/requirements to end users.

#### 4.2.1.7 Biometric Security Credentials, Devices, Registration, Deregistration, Validation and device platform security

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Significant functionality provided by MOSIP - TBD\
**Comments:** Each building block dealing with biometric credentials MUST implement biometric security credential management, registration, deregistrations, re-registration, validation and device platform security etc. such as above for biometric capture devices.

#### 4.2.1.8 Non-repudiation and Certificates (X509, OpenID and SAML etc.)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Likely built-in to API Management and Gateway but may also require certificate server etc. All communications from all clients (web/mobile etc. must be via API)\
**Comments:** Each building block MUST implement a framework for non-repudiable transactions using certificates and federation protocols (X509, OpenID and SAML 2.0 etc.)

#### 4.2.1.9 Single-Sign-On and 3rd Party Security

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Identity/Security\
**Description:** Likely built-in to API Management and Gateway. All communications from all clients (web/mobile etc. must be via API)\
**Comments:** Each building block MUST be able to implement single-sign-on integration with 3rd party security.

### 4.2.2 PROTECT

#### 4.2.2.1 Authentication and Authorization

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All\
**Description:** Applies to all connections throughout all components such as:

Web/Mobile UI<->API, Web/Mobile UI,<->Auth, BB<->API<->BB, Workflow<->API\
**Comments:** Each building block MUST implement SSL and TLS based connections for all TCP connectivity both external to the building block, and internally between components in a selective manner depending on data requirements.

**4.2.2.2 Data Sovereignty/Residency Controls and Hosting, Transmission, Backup and Recovery**

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** All\
**Description:** Probably needs to be addressed during country rollouts due to data sovereignty regulations but needs to be catered for in the architecture options.\
**Comments:** Each building block where dealing with citizens data MUST provide the ability to implement data sovereignty/residency controls, hosting, transmission, backup and recovery in compliance with specific national laws and guidelines in each country.

#### **4.2.2.3 Network Security, Protocols and Firewall implementations**

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Cloud Infrastructure and Hosting\
**Description:** Infrastructure oriented but could be addressed at least in part by software defined networking (SDN) which can be part of a modern PaaS such as OKD \
**Comments:** Each building block shall comply with the overall secure networking architecture that will be deployed in place with each country implementation. Issues such as network security, networking protocols and firewall implementations etc. shall be defined as a part of the recommended architecture showing the various zones and separations required.\


**4.2.2.4 Application Services Security (multi-tenancy etc.)**

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Likely best implemented as a feature of the chosen PaaS framework such as OKD\
**Comments:** The components for each building block are required to be deployed in containers according to the architecture description. The chosen container orchestration platform and PaaS solution shall provide the means to implement Application Services Security (such as multi-tenancy etc.)

#### **4.2.2.5 VPN and Secure Network Access Controls**

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Infrastructure oriented but could be addressed at least in part by software defined networking (SDN) which can be part of a modern PaaS such as OKD\
**Comments:** Each building block MUST comply with a defined set of VPN and Secure Network Access Controls. This will be based on the location of event producers and consumers on the network and hope the various segments of networking are sliced and protected. These standards are to be defined as a part of the target architecture implementation for each country.

#### **4.2.2.6** Network Vulnerability Scanning

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Can be sourced from open source tooling such as OpenVAS, Wireshark etc.\
**Comments:** A suite of open source tools are to be adopted for the purposes of Network Vulnerability Scanning. These tools MUST be acquired by the project and centrally deployed in each country to ensure adequate network service security is in place.

#### **4.2.2.6** Network Vulnerability Scanning

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Can be sourced from open source tooling such as OpenVAS, Wireshark etc.\
**Comments:** A suite of open source tools are to be adopted for the purposes of Network Vulnerability Scanning. These tools MUST be acquired by the project and centrally deployed in each country to ensure adequate network service security is in place.

#### **4.2.2.7** Software Defined Networking and Network Slicing&#x20;

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Infrastructure oriented but could be addressed at least in part by software defined networking (SDN) which can be part of a modern PaaS like OKD\
**Comments:** The project MUST adopt a software defined networking solution as a part of the core deployment architecture. This can and SHOULD be implemented as a part of the chosen PaaS solution.

#### **4.2.2.8** Operating Systems, Services Security and Immutability

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Infrastructure oriented but could be addressed at least in part by OS like Centos which can be part of a modern PaaS such as OKD\
**Comments:** The project MUST deploy all services (typically microservices) on an immutable operating system infrastructure. Typically this can and SHOULD be provided as part and parcel of the chosen PaaS solution. The reason for this is such that if a security breach does happen then the operating system running the component cannot be modified by the offender.

#### **4.2.2.9** Network, Service and Transaction Observability and Visibility

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Can be addressed as part and parcel of a modern PaaS solution such as OKD including a service mesh such as ISTIO\
**Comments:** The project MUST implement a PaaS infrastructure that supports Network, Service and Transaction Observability and Visibility for protection against flaws and faults. This is so that complex transactions involving multiple components (likely microservices) can be observed and traced for the purposes of debugging and auditing. This would typically be implemented at least in part by a service mesh feature of the PaaS along with other integrated components for visualization such as the Jaeger open source tracing facility and the Kiali open source visualizer for example.

#### **4.2.2.10** Man-in-the-middle (MITM) Attack Prevention (AKA Session Hijack)

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low\
**Building Block Mappings:** All\
**Description:** Needs to handle insecure WIFI, email spam filtering, virus scanning and ad-blockers etc. at all levels.\
**Comments:** Needs to handle insecure WIFI, email spam filtering, virus scanning and ad-blockers etc. at all levels.

#### **4.2.2.11** Cloud Platform Configuration Management and Securing Configurations

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All\
**Description:** Can be addressed as part and parcel of a modern PaaS solution such as OKD (which has secure encrypted stores for credentials) \
**Comments:** Each building block MUST adopt the facilities of the chosen PaaS for implementing Cloud Platform Configuration Management and Securing Configurations. For example authentication credentials for common components like databases need to be managed appropriately and simply across multiple environments through DevOps automated deployment etc.

#### **4.2.2.12** Insider threats and internal audit-ability

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** The same security protocols, data encryption, protections and monitoring to be applied consistently both internally and externally. \
**Comments:** Each building block MUST adopt the same consistent security and privacy implementation measures to protect against Insider threats and internal audit-ability as those adopted for external exposures. This is a general statement.

#### **4.2.2.13** Denial of service attack prevention

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** All/Cloud Infrastructure and Hosting\
**Description:** Can be managed by implementing open source tools/services such as CrowdSec and DDOS Deflate, Fail2Ban, HAProxy, DDOSMon, NGINX etc. Note that HAProxy is built into PaaS solutions like OKD - TBD. Note that a number of API Gateway products are built around NGINX\
**Comments:** The project must implement an open source Denial of service attack prevention solution across all interfaces exposed to the public internet for each country deployment. This can be implemented through a reverse proxy web server environment using open source tools such as Fail2Ban, DDOS Deflate or HAProxy.

#### **4.2.2.14** API Endpoint Security Policy Management and Gateway Services (both internal and external)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** The implementation of a centralized API Management and Gateway solution is probably not negotiable. All API interfaces both internal and external must be managed through this facility. Architecture will likely require a separate gateway for both internal and external services.\
**Comments:** The project MUST implement centralized API Endpoint Security Policy Management and Gateway Services (both internal and external). The reason for this is to implement a consistent layer of security for API interfaces that can be both managed centrally and alleviate the service developers from the implementation complexity of security. This can and SHOULD be implemented through an open source API Management and Gateway services product.

#### **4.2.2.15** Virus/Malware and Ransomware Attack Prevention and Detection

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Requires extensive and probably commercial software in many layers.\
**Comments:** The project MUST implement protection from and detection of Virus/Malware and Ransomware Attack. This likely requires a commercial solution suite as open source offerings are insufficient and not suitable for massive country-wide deployments w=such as GovStack.

#### **4.2.2.16** Credential Theft Prevention

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** Can be addressed as part and parcel of a modern PaaS solution such as OKD (which has secure encrypted stores for credentials). Requires implementation through all development procedures and CI/CD etc.\
**Comments:** The project MUST implement credential theft prevention as part and parcel of its selected PaaS infrastructure. This is essentially an encrypted keystore that can host sensitive credentials and provide access to them with policy based security.

#### **4.2.2.17** SQL Injection Attack Prevention

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** Can be addressed through open source tools such as those provided by the OWASP Foundation. Plugins for OWASP tools are available for PaaS solutions like OKD\
**Comments:** The project MUST implement SQL Injection Attack prevention as part and parcel of any and all applications development across building blocks. This can be implemented through open source tools such as those provided by the OWASP Foundation. This can and SHOULD be implemented as plugins through the PaaS solution and fully integrated into the DevOps toolchains for the project build and deployment.

#### **4.2.2.18** Containing, Managing and Mitigating Hardware/Firmware Vulnerabilities and Known Exploits (directory traversal, rowhammer, spectre, meltdown, LazyFP etc.)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low-Medium\
**Building Block Mappings:** Security\
**Description:** Typically these types of attacks are best mitigated by the use of commercial open source subscriptions as they close the window of vulnerability. New CVE’s happen every month and are becoming more common as IT advances. The upstream open source projects like OKD will eventually get the patches but it will be some time after commercial open source product patches are released to those with enterprise subscriptions.\
**Comments:** The project MUST implement solutions for Containing, Managing and Mitigating Hardware/Firmware Vulnerabilities and Known Exploits (directory traversal, rowhammer, spectre, meltdown, LazyFP etc.). This can and SHOULD be implemented through plugins to the PaaS solution and DevOps toolchain for the project to ensure that every single component deployed is scanned for known CVEs.

#### **4.2.2.19** Data Privacy/Loss/Leakage/Confidentiality (individuals and organisations)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** For the most part this involves end-point protection. Some tools are available in open source but it requires multiple layers of implementation and is thus more expensive.\
**Comments:** The project SHOULD implement solutions for prevention against Data Privacy/Loss/Leakage/Confidentiality (individuals and organisations). This likely requires expensive commercial packages rather than open source tooling.

#### **4.2.2.20** Data Security (at rest and in transit - i.e. encryption and obfuscation etc.)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Needs to be considered for each data store and each connection in the architecture. It is a very broad topic that must be addressed in the context of the data confidentiality requirements for each country implementation. Will be relatively expensive for resource-limited settings but it is a necessity.\
**Comments:** The project MUST implement solutions for Data Security (at rest and in transit - i.e. encryption and obfuscation etc.) consistently across all datastores and connections within and surrounding all building blocks.

#### **4.2.2.21** Cross-site Scripting (XSS) Attack Prevention

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** By virtue of the fact that each BB will host its own UI there is strong potential for cross-site scripting vulnerabilities. Rules must be adhered to by developers. For example, all DOM based XSS reflection or embedding must be performed on the server side not in the ECMA layer. Several other rules must also be implemented for developers to reduce the likelihood of XSS vulnerabilities. Many of these rules can be found here on the OWASP web site: [https://cheatsheetseries.owasp.org/cheatsheets/Cross\_Site\_Scripting\_Prevention\_Cheat\_Sheet.html](https://cheatsheetseries.owasp.org/cheatsheets/Cross\_Site\_Scripting\_Prevention\_Cheat\_Sheet.html)\
**Comments:** The project must provide a consistent set of rules for cross site scripting across all building blocks to ensure that it is not exposed to Cross-site Scripting (XSS) Attacks. This is a complex area that must be addressed during development and testing. Details of many of the rules that must be implemented can be found on the OWASP web site.

#### **4.2.2.22** Replication and Perimeter/Edge Data and Services Security

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This is complex and applies to large architectures with multiple data centers and perimeter services. Every single element of the networks and trusts must be examined for vulnerabilities. There is no simple one-shot solution for this as it involves multiple data centers and multiple layers communicating and replicating potentially sensitive data. The degree to which this is addressed is commensurate with the relative sensitivity of the data and services involved.\
**Comments:** The project MUST provide Replication and Perimeter/Edge Data and Services Security. This assumes that practically all national deployments will have multiple sites that must be protected from breaches and leakages as a result of technology services deployed to distribute and consolidate data.

#### **4.2.2.23** Social Media, Social Network and Social Engineering Threats and Prevention

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This is a complex subject that requires not only technical intervention but extensive training for everyone involved in the processes of eGovernment.\
**Comments:** The project MUST provide protection from Social Media, Social Network and Social Engineering Threats. This is not only a technology services issue but also applies to standard operating procedures and requires extensive user education.

#### **4.2.2.24** Centralized PAAS Management, Monitoring and OTA Automated Update

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security/Cloud Infrastructure and Hosting\
**Description:** Can be addressed as part and parcel of a modern PaaS solution such as OKD - TBD (which has over the air update capabilities along with centralized management and monitoring).\
**Comments:** The project MUST provide Centralized PAAS Management, Monitoring and OTA (over-the-air) Automated Update for infrastructure and applications components. This is to ensure that patches to emerging and common vulnerabilities are addressed in the smallest window possible and the whole architecture is not exposed through such vulnerabilities. This can and SHOULD be addressed as part and parcel of the selected PaaS infrastructure.

#### **4.2.2.25** Digital Service Registry Security

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security/Registration\
**Description:** Can be addressed as part and parcel of a modern PaaS solution such as OKD - TBD (which has an embedded services registry) - there may be other registries required that are also impacted. There needs to be careful delineation of functionality and terminology used for registries as there are many implications in PaaS environments such as for service exposure through software defined networks etc.\
**Comments:** The project and all building blocks utilizing registries of any kind (particularly digital service registries) MUST provide Digital Service Registry Security. This means ensuring that the protocols, interfaces and connections to such centralized services are controlled in accordance with the other requirements for connections and API etc.

#### **4.2.2.26** Surrounding Networking Software Infrastructure Security (DNS, DHCP , PXE, BootP services etc.)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security/Cloud Infrastructure and Hosting\
**Description:** Each core network service must be addressed in its own right. There is too much to discuss here but these services are critical, exposed, prone to vulnerabilities and must be secured with the highest possible standards applied.\
**Comments:** The project MUST address the general Surrounding Networking Software Infrastructure Security (DNS, DHCP , PXE, BootP services etc.) for each and every country rollout. These services are particularly vulnerable as some of them are exposed to insecure zones (especially DNS).

#### **4.2.2.27** Cloud Provider Infrastructure Security (hardware layer, infrastructure layer, virtualisation, container and platform layer, application layer)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security/Cloud Infrastructure and Hosting\
**Description:** Each cloud service must be addressed in its own right. There is too much to discuss here but these services are critical, exposed, prone to vulnerabilities and must be secured with the highest possible standards applied.\
**Comments:** The project MUST provide protection against common vulnerabilities in Cloud Provider Infrastructure Security (hardware layer, infrastructure layer, virtualisation, container and platform layer, application layer etc.). This is specific to each public cloud provider where utilized but a common source of threats since they involve complex suites of services that are stitched together (most often by the implementer not the cloud provider) in multiple layers to form the solution architecture.

#### **4.2.2.28** Mobile and Wireless Networking Security/WIPS

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security/Cloud Infrastructure and Hosting\
**Description:** Mobile and wireless networking security is a significant issue to deal with given that there will likely be mobile applications deployed as a part of the architecture. A plethora of issues abound including for example Evil Twin Attack, WarDriving (piggyback attack), sniffing and shoulder-surfing etc.. CISA has released a short guide here for securing wireless in general: [https://us-cert.cisa.gov/ncas/tips/ST05-003](https://us-cert.cisa.gov/ncas/tips/ST05-003)\
**Comments:** The project MUST provide protection against Mobile and Wireless Networking Security/WIPS vulnerabilities. There are many potential and known vulnerabilities around these networks which have predicated information security in the digital age. The potential for eavesdropping and information leakage as well as other forms of hijacking attacks is very broad as the exposure is over-the-air.

#### **4.2.2.29** Compressed and Encrypted Information Transmission via Messaging and Email etc. to external or internal 3rd parties along with any other potential forms of critical information leakage.

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security/Cloud Infrastructure and Hosting\
**Description:** This is principally the same as endpoint security to prevent information leakage.\
**Comments:** The project (including all building blocks MUST provide protection against private information leakage through Compressed and Encrypted Information Transmission via Messaging and Email etc. to external or internal 3rd parties along with any other potential channels for critical private information leakage.

#### **4.2.2.30** Anti-Phishing and Anti-Spam

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Phishing and the associated spam are two of the most common digital platform security problems and must be dealt with. A number of open source solutions exist such as OrangeAssassin, MailScanner and Apache SpamAssassin. These are commonly used by many commercial sites all around the world.\
**Comments:** The project MUST provide Anti-Phishing and Anti-Spam tooling. These are some of the most common sources of security issues and can be dealt with using open source tools such as Orange Assassin, MailScanner and SpamAssassin.

#### **4.2.2.31** Physical Security and Access Controls to Facilities

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Physical security is a must for all on-premise facilities and almost goes without saying. The extent to which physical security is implemented must comply with national government hosting standards in each country.\
**Comments:** The project MUST provide physical security measures for access to physical facilities.

#### **4.2.2.32** Portable and Removable Media Controls

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** This is commonly known as endpoint security and must be dealt with comprehensively either at hardware level (by disconnection) or in software that allows policy and procedure for removable media to be controlled.\
**Comments:** The project MUST provide portable and removable media controls to protect against information leakage.

#### **4.2.2.33** Backup Security and Backup Information Controls

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This is a complex and diverse area to address as there will be several data repositories and databases in the deployed infrastructure including both CUI and regular non-CUI information. Backups are one of the areas that create large exposure for information loss and must be addressed consistently and thoroughly.

This must include encryption of backups and the physical security of backups as well as the policy, procedure and controls to ensure that leakage risk is minimized.\
**Comments:** The project must provide backup information controls and security to prevent information leakage and tampering etc. through the backup and recovery processes. This applies to all building blocks.

### 4.2.3 DETECT

#### **4.2.3.1** Vulnerability Management and Security Automation

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** Several open source and commercial tools are available to address this in terms of scanning for vulnerabilities in all layers of the solution including containers for example. The process and tools for this need to be addressed specifically depending on the technical components of the final solution architecture.\
**Comments:** The project MUST provide tools to detect, manage and automate the resolution of common vulnerabilities in all layers (applications components down to infrastructure components) before they eventuate as deployed in the solution. There are many open source scanning tool options available for this purpose. CISA defines the standards for this and refers to many of the available open source tools.

#### **4.2.3.2** Applications Development, Deployment, DevSecOps and Container Image Security

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This needs to be built-in to the CI/CD process to ensure that only secured images are deployed to production. Most modern PaaS offerings such as OKD - TBD are also shipped with a rudimentary suite of tools to accomplish this.\
**Comments:** The project MUST provide a secure DevSecOps process for code deployment. This applies to areas surrounding Applications Development, Deployment, DevSecOps and Container Image Security scanning (i.e. what's inside the container) before applications components are deployed.

#### **4.2.3.3** Compliance Checking and Scanning (PCIDSS/HIPAA, CIS etc.)

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low-Medium\
**Building Block Mappings:** Security\
**Description:** These are global standards for security compliance checking and several tools are available in the market to address this. Both commercial and open source options are available.\
**Comments:** The project MUST provide tooling support for Compliance Checking and Scanning (PCIDSS/HIPAA, CIS etc.). A number of open source tools and commercial off-the-shelf tools are available for this purpose. This compliance checking MUST be conducted on a regular basis for all building blocks dealing with financial, healthcare and personal data in accordance with the aforementioned PCIDSS, HIPAA and CIS standards.

#### **4.2.3.4** Security Risk Profiling

**Organizational Risk Rating:** Low\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low-Medium\
**Building Block Mappings:** Security\
**Description:** Several tools are available in this space with varied ways of addressing the concerns including threat modeling\
**Comments:** The project SHOULD provide tools for Security Risk Profiling. Several such tools are available and offer assessment of security risks through techniques such as threat modeling.

#### **4.2.3.5** Threat/Intrusion Detection and Prevention

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** Several open source tools are available to address this space admirably including for example Snort, Bro, Kismet, OSSEC and Open DLP etc. These are VERY effective, VERY mature and easily adopted.\
**Comments:** The project MUST deploy tooling for Threat/Intrusion Detection and Prevention in the infrastructure and other layers. Several such tools are available in open source (Snort, Bro, Kismet, OSSEC etc.)

#### **4.2.3.6** Login Notifications and Alerts etc. (new device or IP etc.)

**Organizational Risk Rating:** Medium\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** This should be managed with the basic user device profile and an alert sent via email and other channels whenever a login is made from a new endpoint, giving the user the option to lock the account.\
**Comments:** The project across all building blocks SHOULD provide Login Notifications and Alerts etc. (new device or IP etc.) where email or other notifications would be sent to recipients with warning messages when authentication is performed from a new device. This also involves keeping a registry of registered devices for each user/party/actor (albeit internal or external and the ability for them to lock their account if the authentication was achieved by an unknown party.

#### **4.2.3.7** Open Source Intelligence (OSINT) Platforms/Tools and Processes

**Organizational Risk Rating:** Low\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security\
**Description:** OSINT gathering is COMPLEX. The following article describes the origins and tools of OSINT that have evolved from the original Metasploit (white hacking solution): [https://www.csoonline.com/article/3445357/what-is-osint-top-open-source-intelligence-tools.html](https://www.csoonline.com/article/3445357/what-is-osint-top-open-source-intelligence-tools.html)

Essentially OSINT puts the hackers' tools into the security analysts protection arsenal.\
**Comments:** The project SHOULD provide Open Source Intelligence (OSINT) Platforms/Tools and Processes in order to perform security assessments on open source usage. This essentially incorporates the hackers tools into the protection and detection arsenal (see the evolution of Metasploit and other white hacker solutions in open source).

#### **4.2.3.8** Information gathering and Security Data Visualization

**Organizational Risk Rating:** Low\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low\
**Building Block Mappings:** Security\
**Description:** This is an emerging area of value that largely comprises of the following types of visualizations but there are no comprehensive open source tools available:

Perimeter Threat

Network Flow Analysis

Firewall Visualization

IDS/IP S Signature Analysis

Vulner ability Scans

Proxy Data

User Activity

Host-based Data Analysis\
\
**Comments:** The project SHOULD provide tooling for Information gathering and Security Data Visualization for maintaining security observability through operations. Many different visualizations are available through various commercial tools but no comprehensive open source solution is available.

#### **4.2.3.9** Fraud Detection and Management

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Fraud detection and management is the set of activities carried out to check money or property from being acquired through false pretenses is known as fraud detection and the ability to trace and manage incidences of fraud. In many industries like banking or insurance, fraud detection is applied. SInce this project involves money exchange there is a case for fraud detection and management. Number of open source tools including the following are available: FraudLabs Pro, Fraud.Net, MISP, pipl, Sift etc.. See this article for a deeper description: [https://www.goodfirms.co/blog/best-free-open-source-fraud-detection-software](https://www.goodfirms.co/blog/best-free-open-source-fraud-detection-software)\
**Comments:** The project MUST provide tooling for Fraud Detection and Management. This is not negotiable and many open source tool sets currently exist such as FraudLabs, Fraud.Net and MISP. This applies to all building blocks dealing with financial transactions and information (such as payments - which appears to be bidirectional… i.e. govt-to-recipient and payee-to-govt).

### 4.2.4 RESPOND

#### **4.2.4.1** Incident Response and Management - applies to attempted and successful intrusion, fraud, hacking, phishing incidents and all other forms of security incident

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** Incident Response and Management (ticketing etc.) - applies to attempted and successful intrusion, fraud, hacking, phishing incidents and all other forms of security incident\
**Comments:** The project MUST provide Incident Response and Management (ticketing etc.) - This applies to both attempted and successful intrusion, fraud, hacking, phishing incidents and all other forms of security incident. This applies across all building blocks and must be built-in to the infrastructure and processes of each building block when any incident is detected.

#### **4.2.4.2** Security Sandbox Solution - used to test responses to potential/predicted security incidents

**Organizational Risk Rating:** Low\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low\
**Building Block Mappings:** Security\
**Description:** This would involve creating a sandbox environment to test and resolve security issues thus requiring a complete sandbox of all the security tools mentioned here.\
**Comments:** The project MUST provide a Security Sandbox Solution - used to test responses to potential/predicted and actual security incidents.

### 4.2.5 RECOVER

#### **4.2.5.1** Critical digital infrastructure business continuity considerations (terrorism, sabotage, information warfare, natural disasters etc.) - processes and how to recover digital infrastructure.

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Low-Medium\
**Building Block Mappings:** Security\
**Description:** This is more of a planning and execution exercise and simply must be built-in to the overall deployment game plan for every single piece of software infrastructure and data infrastructure along with the processes and procedures as well as test recoveries to ensure that an adequate recovery response can be attained on demand.\
**Comments:** The project MUST deal with Critical digital infrastructure business continuity considerations (terrorism, sabotage, information warfare, natural disasters etc.) - i.e. provide the technical ability and processes required in order to recover the complete digital infrastructure. This applies to all building blocks and must also endure recovery testing on a regular basis.

#### **4.2.5.2** Specifically Security Related Concerns surrounding BIA/DRP/BCP (disaster recovery, business continuity etc.) - how to recover to specific data versions using logging tracking and tracing information to determine the best path.

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This is similar or the same as the concern above and simply elaborates it further.\
**Comments:** The project MUST deal with Specifically Security Related Concerns surrounding BIA/DRP/BCP (disaster recovery, business continuity etc.) - what this means is how to recover to specific data versions using logging, tracking and tracing information to determine the best recovery path. This also covers the security of the backups themselves to prevent fraud, tampering and information leakage during storage or recovery for example and MUST address the exact data security requirements stipulated throughout this document but in the context of backups.

#### **4.2.5.3** Cloud Security Posture Management (automation of identification and remediation of risks with public cloud services)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Low-Medium\
**Building Block Mappings:** Security\
**Description:** This is a more advanced and aggregated way of determining the overall security posture in respect to public cloud based deployments and takes into account all of the risks. There are a number of open source solutions available such as OpenCSPM (cloud security posture management). Really only applicable with deployments on public clouds but becoming essential.\
**Comments:** The project SHOULD implement Cloud Security Posture Management (automation of identification and remediation of risks with public cloud services). Open source tools such as OpenCSPM are available.

#### **4.2.5.4** Digital Service Registry State Recovery

**Organizational Risk Rating:** High\
**Target Deployment Phase:** First\
**Feasibility for Limited/Low Resource Settings:** High\
**Building Block Mappings:** Security/Registry\
**Description:** It seems the concept of registry is morphing into something more generic than it was originally (which seemed to be a service registry). The state recovery for this is contingent on the technology solution that the Registration BB takes. Losing the state of this registry due to a security issue is a key risk that MUST be mitigated.\
**Comments:** The project MUST provide the ability for specific Digital Service Registry State Recovery (point-in-time). Registries are one of the most likely early targets of cyber-criminals. This applies predominantly to the Registry building block.

#### **4.2.5.5** Controlled Unclassified Information (CUI) Registries, Repositories and Processes (i.e. marking, safeguarding, transporting, disseminating, reusing and disposing of controlled unclassified information)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** This is all about how information is controlled throughout systems based on its secrecy/privacy classification.

We have made an assumption that GovStack will only ever have to deal with what is known as CUI ([Controlled Unclassified Information](https://www.archives.gov/cui)) as opposed to CI (Classified Information - which is the type of information managed by security agencies such as the CIA).

CUI MUST be managed in accordance with NIST [SP 800-171 Rev. 2](https://csrc.nist.gov/publications/detail/sp/800-171/rev-2/final)\
**Comments:** This is a bit more general but the project SHOULD provide the ability to manage and recover Controlled Unclassified Information (CUI) Registries, Repositories and Processes (i.e. marking, safeguarding, transporting, disseminating, reusing and disposing of controlled unclassified information). This is to be in accordance with NIST 800-171 Rev.2 (see References and Standards). This applies to all building blocks that deal with CUI (usually information collected by govt and security agencies) which is likely to also be specific to country implementation.

#### **4.2.5.6** Controlled Unclassified Information (CUI) domain isolation (isolation for sub-networks and security domains etc. handling CUI)

**Organizational Risk Rating:** High\
**Target Deployment Phase:** Second\
**Feasibility for Limited/Low Resource Settings:** Medium\
**Building Block Mappings:** Security\
**Description:** See above - requires a physically separate domain for hosting such information.\
**Comments:** This is related to the above but the project SHOULD provide Controlled Unclassified Information (CUI) domain isolation (isolation for sub-networks and security domains etc. handling CUI).\
\




