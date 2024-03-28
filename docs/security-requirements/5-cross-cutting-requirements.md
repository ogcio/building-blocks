# 5 Cross-Cutting Requirements

Note that all of the requirements stipulated in this document and its references are reciprocal in that they also apply to components such as the API Management and Gateway services implemented by the security building block. For example the API Management and Gateway services deployed by this building block MUST also address their own intrusion prevention and detection needs referencing the solution requirements defined by this document.

The requirements stipulated in this document are themselves cross-cutting in that they apply to all building blocks and MUST be cross-referenced by the Building Block Definitions for each building block in the Cross-cutting requirements section.

Having these cross-cutting requirements defined centrally in this document and its references removes the issues of inconsistent, insufficient, costly and repetitive security implementation across all building blocks.

The cross-cutting requirements described in this document, its references and this section are an extension of the high level cross-cutting requirements defined in the architecture specification document and intended to specifically define the security requirements for the whole GovStack architecture in all layers.

This section describes the additional cross-cutting requirements that apply to the security building block as well as cross-cutting security requirements for ALL other building blocks. Note that cross-cutting requirements defined here use the same language (MUST or SHOULD) as specified in the architecture blueprint document (see [<mark style="color:blue;">Ref 1</mark>](https://docs.google.com/document/d/1Z9jS0BnfTM3azBED5349uD5sQ9VYYo8p/edit#heading=h.k32er9gmkfp0)).

## 5.1 Privacy

Personal data MUST be kept private and never shared with any parties, except where specific authorization has been granted. This also applies to all acquired security components as they will often be logging personal data along with the transactional records. That logging data must also be considered private. Where CUI (Controlled Unclassified Information) is dealt with, the NIST 800-171 Rev 2 standard shall be applied (see [Ref 3](https://docs.google.com/document/d/1Z9jS0BnfTM3azBED5349uD5sQ9VYYo8p/edit#heading=h.k32er9gmkfp0))

## 5.2 Security Requirements

Must refer reciprocally to this document and its references.

Security requirement is a condition over the phenomenon of the environment that we wish to make true by installing the system in order to mitigate risks. A requirement defining what level of security is expected from the system with respect to some type of threat or malicious attack.

## 5.5 Digital ID/Certificate Functional Requirements

<table data-header-hidden><thead><tr><th width="636"></th><th width="131"></th></tr></thead><tbody><tr><td><p><strong>5.5.1 Enrollment Services</strong></p><p>Enrollment services for a digital ID in the form of a certificate using the physical credentials of the enrollee (a human citizen subject) and the process of the Identity BB (see the functional requirements for Identity in the Identity BB Definition). A feature for invalidating, locking or disenrollment/revocation of the digital ID shall also be provided as a response measure to both human citizen subjects leaving the system and responding to security breaches encountered. Digital certificate enrollment must be provided by the solution but is not required for every human citizen subject (see below).<br></p><p>Note that it is anticipated that the Identity BB will call this feature either directly via API or indirectly via the IAM features of the Security BB for users electing to use a digital ID consisting of certificates as a part of the account provisioning process. The digital ID will then be stored with the physical ID records in the identity BB and sent to the new user via secure means (probably installed on their device).<br></p><p>Note that simple numerical digital IDs will also be supported for human citizen subjects as an option where users are unable to leverage certificates based digital ID. The requirements governing this are to be stipulated by the Identity BB (see the Identity BB Definition) .<br></p><p>Note that 3rd party organization and internal subjects (both human and non-human) MUST be issued valid signed digital certificates in order to establish and maintain secure inter-organization and internal communications.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.5.2 Multi-Factor Authentication</strong></p><p>The overall solution suite shall also be able to implement multi-factor authentication using simple numeric digital IDs for human citizen subjects such as their tax file or social security number of the user.<br></p><p>A selection of various alternatives for digital ID is required in order to cater for more or less digitally-savvy citizens. Various token types are also required to be optimally supported such as HOTP and TOTP tokens, SMS, email, push notifications, SSH keys, X.509 certificates, Yubikeys, Nitrokeys, U2F and WebAuthn. Vendors of solutions SHOULD articulate the benefits of what they propose in their solution.<br></p><p>Note that multi-factor authentication must be able to be implemented for both external and internal subjects (people, systems, components etc.) but is not necessarily required for internal non-human subjects (such as building block components) as they communicate via the information mediator BB (see the InfoMed BB Definition).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.5.3 Numerical Digital ID Attribute</strong></p><p>Where human citizen subjects adopt the use of a simple numerical digital ID, the multi-factor authentication process MUST include a time-sensitive credential (AKA OTP or one time PIN)</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.6 Certificate Authority Functional Requirements

<table data-header-hidden><thead><tr><th width="637"></th><th width="118"></th></tr></thead><tbody><tr><td><p><strong>5.6.1 Strong Authentication and Cryptography</strong></p><p>The basic security service requirements of high confidentiality, high integrity, strong authentication, strong cryptography and absolute non-repudiation must be delivered by the solution. The vendor must articulate how these needs are met with the proposed solution suite to ensure that GovStack is able to deliver the same consistent security service experience</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.2 Standards Based Certificate Authority Server</strong></p><p>A certificate authority (CA), or certifier with fully configured server infrastructure, is required to implement trusted administration tools that issue signed digital certificates to citizens and other 3rd parties then maintain the lifecycle of those digital certificates<br></p><p>Digital certificates MUST comply with the IETF, ISO/IEC/ITU-T X.509 Version 3 and PKIX (note that PKIX is the registration authority role, which allows administrators to delegate the certificate approval/denial process) standards as defined by RFC5280 and associated standards. Digital certificates are to be issued on behalf of the appropriate government authority where GovStack is to be deployed.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.3 Certificate Issuance</strong></p><p>Issued signed digital certificates MUST verify the identity of an individual, a server, or an organization and allow them to use SSL to communicate and to use S/MIME to exchange mail as well as sign documents and transactions in a non-repudiable manner.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.4 Digital Signatures</strong></p><p>Certificates issued by the authority MUST be stamped with the certifier's digital signature (i.e. signed), which assures the recipients of the certificate that the bearer of the certificate is the entity named in the certificate.</p></td><td><p>REQUIRED</p><p><br></p></td></tr><tr><td><p><strong>5.6.5 Private Certifier Capability</strong></p><p>The solution provided MUST be able to be set up as a certifier to avoid the expenses that a third-party certifier charges to issue and renew client and server certificates. In other words the solution can operate without a 3rd party certifier. This makes it easier, cheaper and quicker to set up and deploy new certificates as needed and at scale. Certificate validation will not be required to access a 3rd party certifier for validation.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.6 Revocation Lists Support</strong></p><p>The certificate server MUST be able to support certificate revocation lists (CRLs), which contain information about revoked or expired Internet certificates.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.7 Flexible Certificate Authority Hierarchy</strong></p><p>The certificate authority server infrastructure MUST enable CA administrators to create a flexible private CA hierarchy, including root and subordinate CAs, with no need for external CAs.</p><p>Private CA hierarchies must be able to be built in a hybrid mode, combining online and on-premises CAs with cloud based CAs.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.8 Web Based Admin Interface</strong></p><p>The certificate authority server infrastructure MUST provide a comprehensive web based administrator user interface so that all of the GovStack certificate issuance and revocation features and functions can be configured and managed from a single central window.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.9 Standards Based API Interface</strong></p><p>The certificate authority server infrastructure must provide a secure API interface that supports calls for the issuance and revocation of certificates by other GovStack components such as the Identity Building Block. This API must comply with the same OpenAPI standards defined in the Architecture Blueprint (see <a href="https://docs.google.com/document/d/1Z9jS0BnfTM3azBED5349uD5sQ9VYYo8p/edit#heading=h.k32er9gmkfp0">Ref 1</a>)</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.10 High Availability</strong></p><p>The certificate authority server and its infrastructure must be configurable for highly available implementation (see the non-functional definitions for high availability). For example this means clustering and failover of certificate authority services and associated data sources to provide a 24x7x365 service with 99.99% availability (AKA 4 nines)..</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.11 Horizontal Scalability</strong></p><p>The certificate authority infrastrastructure must be horizontally scalable on commodity hardware to ensure that the scalability needs of low resource countries with large populations deploying GovStack can be met without incurring significant or untenable costs.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.12 Advanced Encryption Methods Support</strong></p><p>The solution provided MUST support advanced encryption techniques such as ECC (Elliptic Curve Cryptography) which gives certificates an additional security/performance advantage vs use of the traditional RSA cryptography system for example. Other techniques may be acceptable and the vendor must explain and justify why they are superior.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.13 Enrollment via API Interface (SCEP)</strong></p><p>The solution MUST provide a means of enrollment via a standardized API interface which SHOULD be based on SCEP. A description of the OpenXPKI enrollment workflow and API can be found here: <a href="https://openxpki.readthedocs.io/en/latest/reference/configuration/workflows/enroll.html">https://openxpki.readthedocs.io/en/latest/reference/configuration/workflows/enroll.html</a>. This is an example only and can vary based on the proposed implementation.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.6.14 Security Provisions</strong></p><p>The certificate authority deployment scheme must be exposed to the public internet and protected securely in accordance with all of the other security requirements and provisions described in this document. The reason for this is to allow 3rd parties to verify the authenticity of certificates issued by the govts deploying GovStack.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.7 Credential Storage (i.e. LDAP) Functional Requirements

<table data-header-hidden><thead><tr><th width="632"></th><th width="118"></th></tr></thead><tbody><tr><td><p><strong>5.7.1 Centralized Credential Store</strong></p><p>The GovStack security solution requires a credential store as a centralized infrastructure for hosting the user account and credentials defined such that the IAM solution and other components such as the API Management and Gateway solutions can leverage them. This may end up being embedded in other solutions such as IAM or potentially implemented as a separate repository such as LDAP.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.7.2 Web Based Admin Interface</strong></p><p>The solution provided as a credential store MUST have a comprehensive web based administrative interface that allows administrators to make any necessary configuration changes and modify credentials for subjects as needed.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.7.3 High Availability</strong></p><p>The solution provided as a credential store and associated components providing access to the store MUST be highly available and utilize clustering technology in order to provide a minimum of 24x7x365 service with 99.99% availability (AKA 4 9’s).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.7.4 Standards Based REST API</strong></p><p>The solution provided MUST include a standard API for storage and access to credentials such as the standard REST LDAP API provided by the open source 389 Directory Server here: <a href="https://directory.fedoraproject.org/docs/389ds/design/ldap-rest-api.html#ldap-rest-api">https://directory.fedoraproject.org/docs/389ds/design/ldap-rest-api.html#ldap-rest-api</a> . Note that this is purely an example and may vary based on the solution proposed.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.7.5 Standard Connectors and Adapters</strong></p><p>The solution provided as a credential store must be fully integratable with the other security solution components through standards based protocols and out-of-the-box adapters for the specific product offered.</p></td><td>REQUIRE</td></tr></tbody></table>

## 5.8 Time Sensitive Credential (i.e. OTP) Functional Requirements

<table data-header-hidden><thead><tr><th width="634"></th><th width="131"></th></tr></thead><tbody><tr><td><p><strong>5.8.1 OTP and Multifactor Capability</strong></p><p>The solution must provide the ability to generate and utilize time sensitive credentials in various forms for the purposes of securing user authentication with multiple factors using non-PKI credentials (see the section of digital ID in this document).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.8.2 Multiple OTP Methods</strong></p><p>Multiple methods SHOULD be provided for the implementation of time-sensitive OTP using potentially push or device level sources.</p><p>Note that vendors SHOULD articulate the benefits of their technology and approach to implementing time sensitive credentials and align their recommendations to the needs of resource limited settings.</p></td><td>OPTIONAL</td></tr><tr><td><p><strong>5.8.3 High Availability</strong></p><p>The solution provided as an OTP server and any associated components MUST be highly available and utilize clustering technology in order to provide a minimum of 24x7x365 service with 99.99% availability (AKA 4 9’s).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.8.4 Standards Compliance</strong></p><p>The solution offered MUST comply with at least one of the common OTP related IETF standards such as , RFC 1760 (<a href="https://en.wikipedia.org/wiki/S/KEY">S/KEY</a>), RFC 2289 (OTP), RFC 4226 (<a href="https://en.wikipedia.org/wiki/HOTP">HOTP</a>) and RFC 6238 (<a href="https://en.wikipedia.org/wiki/Time-based_One-time_Password_Algorithm">TOTP</a>).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.8.5 Standards Based REST API</strong></p><p>The offered solution MUST provide a REST API for managing OTP similar to the following: <a href="https://www.miniorange.com/step-by-step-guide-to-set-up-otp-verification">https://www.miniorange.com/step-by-step-guide-to-set-up-otp-verification</a>. This is just an example and can vary with the proposed implementation.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.9 Network Scanning and Vulnerability Management Requirements

<table data-header-hidden><thead><tr><th></th><th width="125"></th></tr></thead><tbody><tr><td><p><strong>5.9.1 Network Policy Definition and Scanning</strong></p><p>The solution offered MUST provide advanced policy definition capabilities along with the ability to scan entire networks and subnetworks with one click and the ability to automate scanning on a regular schedule.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.2 Broad Suite of CVE Scan Coverage</strong></p><p>The solution MUST provide the broadest possible suite of CVE (known vulnerability) scans across common ports for common software services and the like.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.3 Regular CVE Pattern Updates</strong></p><p>The solution must provide regular updates and new plugins for emerging CVEs within a short timeframe of the CVE becoming known.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.4 List of Top Threats and Remediations</strong></p><p>The solution MUST be able to assemble lists of top threats from scans, based on VPR and provide recommendations on which vulnerabilities pose the greatest risk in order to prioritize remediation efforts.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.5 Broad Range of Preconfigured Templates</strong></p><p>The solution MUST provide preconfigured templates out-of-the-box for a broad range of IT and mobile assets. These must support everything from configuration audits to patch management effectiveness which helps quickly understand where vulnerabilities exist and assess audit configuration compliance against CIS benchmarks and other best practices.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.6 Customizable Views</strong></p><p>The solution MUST provide the ability to easily create reports based on customized views, including specific vulnerability types, vulnerabilities by host or by plugin. MUST be able to create reports in a variety of formats (such as HTML, csv and XML) and then easily tailor and email reports to stakeholders with every scan.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.7 Associative Remediation</strong></p><p>The solution SHOULD provide associative remediation via security patch automation using automation tools so that hundreds or even thousands of specific vulnerability instances can be addressed across the whole infrastructure.</p></td><td>OPTIONAL</td></tr><tr><td><p><strong>5.9.8 Standards Compliance Management</strong></p><p>The solution MUST provide the general ability to implement vulnerability management processes that drive compliance with PCI, HIPAA, GLBA, CIS, NIST and or similar European or African continental standards.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.9.9 Scalability</strong></p><p>The offered solution MUST be able to scan whole large networks of computers with thousands of open ports and services within an acceptable time frame (the usual maintenance window). The vendor is to explain the scaling strategy and how it can be used to address a significant eGovernment infrastructure that serves millions of citizens..</p></td><td>REQUIRED</td></tr></tbody></table>

5.10 Virus, Ransomware, Malware, Spam, Phishing Protection Requirements\\

<table data-header-hidden><thead><tr><th width="633"></th><th width="117"></th></tr></thead><tbody><tr><td><p><strong>5.10.1 Transparent Gateway Service</strong></p><p>The solution MUST provide an anti-spam mail gateway that transparently operates within the email routing infrastructure using standards based protocols such as SMTP, POP and IMAP.</p></td><td><br>REQUIRED</td></tr><tr><td><p><strong>5.10.2 Common Vulnerability Scans</strong></p><p>The solution must be able to scan emails for various types of malware and for spam, phishing, and other types of malware common attacks that target known system infrastructure vulnerabilities. The solution must be extensible (perhaps by plugin) to support emerging threats, new vulnerabilities and new services.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.10.3 Cloud or On-Premise Deployment</strong></p><p>The solution MUST provide a cloud-based or on-premise based pre-perimeter defense against spam, phishing emails and virus-infected attachments.</p></td><td>REQUIRED<br></td></tr><tr><td><p><strong>5.10.4 3rd Party Virus Checker Support</strong></p><p>The solution provided MUST support a wide range of 3rd party and open source virus checker software which is independent of the mail scanner module.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.10.5 Wide Range of Filtering Approaches</strong></p><p>The solution provided MUST support a wide range of filtering approaches and analytic tests such as text analysis, DNS blacklists, collaborative filtering databases and Bayesian filtering.</p></td><td><br>REQUIRED</td></tr><tr><td><p><strong>5.10.6 Common Infrastructure Deployments</strong></p><p>The solution MUST be deployable within common open source mail server infrastructures such as procmail, qmail, Postfix, and sendmail</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.10.7 Ability to Integrate in Multiple Points</strong></p><p>The mail scanning modules of the solution MUST be able to be integrated at any place in the email stream.</p></td><td><br>REQUIRED</td></tr><tr><td><p><strong>5.10.8 Multiple Analytic Techniques</strong></p><p>The solution MUST provide multiple analytic techniques, as well as in-depth human expertise, to score incoming email attachments as good, bad, or unknown</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.10.9 Attachment Containment</strong></p><p>The solution MUST run unknown attachment files in containment which is a completely virtual environment and isolated from other network segments.</p></td><td><br>REQUIRED</td></tr><tr><td><p><strong>5.10.10 Day Zero Infection Prevention</strong></p><p>The solution MUST provide the ability to protect from “day zero” infections by rapidly responding with automated updates to counter newly identified threats and applying pattern based algorithms to detect new threats before they infiltrate systems.</p><p>Note: vendor to explain the value proposition of what they offer in this area.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.11 Denial of Service Attack Prevention Requirements

<table data-header-hidden><thead><tr><th></th><th width="116"></th></tr></thead><tbody><tr><td><p><strong>5.11.1 Application Layer Protection</strong></p><p>The proposed solution MUST protect against application layer DDOS attack: Application Layer DDOS attack is a type of DDOS attack which targets the application layer of OSI model (i.e. the protocols that interface software modules such as POP, IMAP, SMTP, HTTP etc.). The size of these attacks are typically measured in requests per second (RPS) and limits must be configurable for both the singular IP addresses and subnets from which such traffic originates.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.2 Protocol Style Attack Prevention</strong></p><p>The proposed solution MUST protect against Protocol style DDOS attacks: Protocol style DDOS attacks target server resources rather than bandwidth through saturation of requests synch as TCP SYN for connection attempts and general UDP frames in order to render the target services useless for users. The size of these attacks are typically measured in protocol frames per second (PFPS) and limits must be configurable for both the singular IP addresses and subnets from which such traffic originates.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.3 Volume Based Attack Prevention</strong></p><p>The proposed solution MUST protect against volume based DDOS attack: Volume based DDOS attack uses a variety of different techniques to saturate bandwidth of the attacked site, so other visitors cannot access it. It eventually leads the server to crash due to traffic saturation. There are three ways the solution MUST defend against volume based DDOS: 1) Attack Prevention and Preemption: this is before the attack based on detection of patterns. 2) Attack Detection and Filtering: This is performed during the attack and packets are filtered or dropped in order to preserve system integrity and 3) Attack Source Blacklisting: This can be performed during and after the attack.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.4 White Lists</strong></p><p>The proposed solution MUST support a white-list of addresses that will always be passed to the servers. This is to facilitate normal usr operations and reduce the likelihood of false positives.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.5 Automatic Unblocking</strong></p><p>Blacklisted or blocked IP addresses MUST be able to be automatically unblocked by the solution after a configurable timeout period.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.6 Remediation Script Hooks</strong></p><p>The solution MUST provide the ability to run hooks for remediation scripts at event edges or at defined intervals for the purpose of cleaning up server resources and ensuring system stability etc.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.7 Alerting Framework</strong></p><p>The solution MUST provide an alerting framework (via email and/or instant messaging) when IP addresses are blocked so that administrators are kept abreast of potential attacks and can begin monitoring activity more closely with a view to manually intervene if necessary.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.8 Standard Firewall Integration</strong></p><p>The solution MUST support and integrate with typical Linux firewall technologies such as APF (advanced policy firewall), CSF (config server firewall) and standard Linux iptables having the ability to insert and adjust rules into the firewall on the fly to cater for attack responses and remediation.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.11.9 TCP Kill</strong></p><p>The solution MUST provide the ability to kill TCP request processes upon encountering flooding in order to preserve the integrity of the protocol stack and return the system to a normal state where it is able to process TCP requests.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.12 Applications Development Vulnerability Prevention Requirements

<table data-header-hidden><thead><tr><th width="635"></th><th width="126"></th></tr></thead><tbody><tr><td><p><strong>5.12.1 OWASP Compliance</strong></p><p>The custom developed applications solutions MUST take steps to protect against the top OWASP vulnerabilities such as XSS for example. Development processes MUST implement automated tooling to check code for such vulnerabilities.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.12.2 OWASP Source Code Scans</strong></p><p>The solution provided MUST be able to scan source code committed to repositories by developers to identify and remediate the top OWASP vulnerabilities. Security hotspots pertain to the implementation of security sensitive code. Detection and human review using developer workflow is required to ensure that defects pertaining to security hotspots do not find their way into production code..</p><p>As developers code and consequently deal with security hotspots, they MUST also be able to learn how to evaluate security risks by example and error identification whilst continuously adopting better secure coding practices. The tooling provided for this MUST enable such a scenario to take place to drive continuous developer security improvement.</p><p>Note that this pertains to custom coding for applications and components developed by all building blocks and not to the code behind 3rd party components and applications to which GovStack must be integrated.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.12.3 Support for Common Programming Languages</strong></p><p>The solution provided should support common programming languages used in the enterprise such as Java, JavaScript, C, C++, C#, Python, Scala, Kotlin, Golang and PHP.</p></td><td>OPTIONAL</td></tr><tr><td><p><strong>5.12.4 Detection and Remediation of Top 10 Vulnerabilities</strong></p><p>The solution provided must minimally support the detection and remediation of the following types of security vulnerabilities (based on the OWASP Top 10 for 2021)::</p><ul><li>Injection (all types)</li><li>Broken authentication</li><li>Sensitive data exposure</li><li>XML External Entities (XEE)</li><li>Broken access control</li><li>Security misconfiguration</li><li>Cross site scripting (XSS)</li><li>Insecure object deserialization</li><li>Libraries/components with known vulnerabilities</li><li>Lack of logging and monitoring</li><li>Generally poor coding practices in memory management etc.</li></ul></td><td>REQUIRED</td></tr><tr><td><p><strong>5.12.5 Common Developer Tools and Frameworks</strong></p><p>The solution provided MUST integrate with common developer tools and frameworks as well as source code control systems such as GIT, SVN etc. and Jira for full cycle issue management.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.13 Infrastructure Vulnerability Remediation Requirements

<table data-header-hidden><thead><tr><th width="630"></th><th width="116"></th></tr></thead><tbody><tr><td><strong>Functional Requirement</strong></td><td><p><strong>Type (Must/</strong></p><p><strong>Should/</strong></p><p><strong>May)</strong></p></td></tr><tr><td><p><strong>5.13.1 Container Scanning Features</strong></p><p>The solution for containers (Docker and OCI) is presumed to be the main infrastructure layer for the project and it is this layer that requires protection from common vulnerabilities and exposures (CVE). The solution for containers MUST provide scanning tools to scan the content of deployed containers for known vulnerabilities with a view to reduce the attack surface for attackers.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.13.2 Fully Integrated DevSecOps</strong></p><p>The solution for containers MUST have a fully integrated DevSecOps approach for CI/CD (continuous integration and continuous deployment) that prevents containers with known vulnerabilities from being deployed and enables patches for known CVE to be deployed both inside the container and to the container orchestration layer and its associated components (AKA PaaS).</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.13.3 Automatic Infrastructure Update</strong></p><p>The solution for containers MUST address the problem of automatically updating the infrastructure on a regular and/or demand basis to apply security patches for known vulnerabilities as soon as they are available. The goal is to reduce the window of vulnerability for new CVE’s that are discovered. This is particularly in consideration of historical vulnerabilities that impacted hardware such as Spectre which impacted over 40M computers worldwide.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.13.4 FIPS 140-2 and ECC Certifications</strong></p><p>The solution for container orchestration and its associated platform infrastructure MUST be certified as compliant with known security standards such as NIST FIPS 140-2 and the European Common Criteria certifications.</p></td><td>REQUIRED</td></tr></tbody></table>

### 5.14 Data Loss and Leakage Prevention Requirements <a href="#docs-internal-guid-53684605-7fff-4057-c5c5-75733534a58a" id="docs-internal-guid-53684605-7fff-4057-c5c5-75733534a58a"></a>

<table data-header-hidden><thead><tr><th width="628"></th><th width="118"></th></tr></thead><tbody><tr><td><strong>Requirement</strong></td><td><strong>Type (Must/ Should/ May)</strong></td></tr><tr><td><p><strong>5.15.1 Multi-Channel Detection and Prevention</strong></p><p>The solution MUST provide a multi-channel means of detecting and preventing data leakage for critical and private data over web, email, instant messaging, file transfer, removable storage devices and printers and any other file transfer means.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.15.2 Fully Controlled Endpoint Protection</strong></p><p>The solution MUST provide endpoint protection for data in use on systems that run on internal end-user workstations or servers. Endpoint-based technology MUST address internal as well as external communications. Endpoint technology MUST be used to control information flow between groups or types of users. It MUST also control email and instant messaging communications before they reach the corporate archive and block communication/consumption/transmission/forwarding of critical and sensitive data.</p><p><br></p><p>The solution MUST monitor and control access to physical devices (such as mobile devices with data storage capabilities - best to restrict mobile access) and restrict access information before it is encrypted (either in situ or in transit). The solution MUST provide the ability to implement contextual information classification (for example identifying what CUI is, or buy identification of the source or author generating content.</p><p><br></p><p>The solution MUST provide application controls to block attempted transmissions of confidential information and provide immediate user feedback with logging and alerts to prevent or intercept future attempts through other channels. The endpoint solution MUST be installed on every workstation (laptop and mobile having access also) in the network (typically via a DLP Agent). Typically it pays to ensure that mobile devices are restricted from such access.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.15.3 Confidential Information Identification</strong></p><p>The solution MUST include techniques for identifying confidential or sensitive information. Sometimes confused with discovery, data identification is a process by which organizations use a data leakage prevention technology to determine what to look for.</p><p>Data is classified as either structured or unstructured. Structured data resides in fixed fields within a file such as a spreadsheet, while unstructured data refers to free-form text or media in text documents, PDF files and video etc.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.15.4 Ability to Implement Compliance Audits</strong></p><p>The solution MUST provide the general ability to implement data loss and leakage prevention processes that drive compliance with PCI, HIPAA, GLBA, CIS, NIST and or similar European or African continental standards.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.15 Data Encryption at Rest and In Transit Requirements

<table data-header-hidden><thead><tr><th width="633"></th><th width="114"></th></tr></thead><tbody><tr><td><strong>Functional Requirement</strong></td><td><p><strong>Type (Must/</strong></p><p><strong>Should/</strong></p><p><strong>May)</strong></p></td></tr><tr><td><p><strong>5.15.1 Support for Standards Based Data at Rest Encryption</strong></p><p>The solution (all components hosting sensitive data, personal data, credit card data or CUI) is required to be able to support the encryption of data at rest using standard strong encryption techniques such as ECC and RSA with certificate based PKI (i.e. X509 etc.). The certificates and PKI infrastructure used for this purpose MUST comply with the requirements stipulated in this document for digital identity.<br></p><p>The solution vendors for 3rd party components should articulate how each of the components supplied provides data encryption facilities for data at rest and the strength and benefits of their approach. This also applies to all components hosting data for all building blocks.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.15.2 Support for Standards Based Data in Transit Encryption</strong></p><p>All of the internal connections between the various components in each building block and between building blocks as well as the external connections for API calls etc. between web and mobile applications and their respective services must be encrypted for data in transit using standard strong encryption techniques such as ECC and RSA with certificate based PKI (ie. X509 etc.). The certificates and PKI infrastructure used for this purpose MUST comply with the requirements stipulated in this document for digital identity.<br></p><p>The solution vendors for 3rd party components should articulate how each of the components supplied provides data encryption facilities for data in transit and the strength and benefits of their approach. This also applies to all components communicating data between all building blocks.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.16 Social Network, Media and Engineering Threat Management Requirements

<table data-header-hidden><thead><tr><th></th><th width="130"></th></tr></thead><tbody><tr><td><strong>Functional Requirement</strong></td><td><p><strong>Type (Must/</strong></p><p><strong>Should/</strong></p><p><strong>May)</strong></p></td></tr><tr><td><p><strong>5.16.1 Social Threat Mitigation</strong></p><p>The project MUST mitigate these types of threats with a combination of policy, training and technology. Many of the attacks in this style are initiated through phishing and dangerous email attachments. It is therefore anticipated that much of the technical aspects of mitigating these types of attacks can be addressed through the requirements identified elsewhere in this document.<br></p><p>Cyber-criminals use a range of attack styles leveraging social networking, engineering and media to achieve a range of goals: for example to obtain personal data, hijack accounts, steal identities, initiate illegitimate payments, or convince the victim to proceed with any other activity against their self-interest, such as transferring money or sharing personal data”<br></p><p>The most frequent styles of attack include:</p><ul><li><a href="https://searchsecurity.techtarget.com/definition/phishing">Phishing</a> – Email or social media based social engineering attacks.</li><li><a href="https://searchunifiedcommunications.techtarget.com/definition/vishing">Vishing</a> – Voice-based social engineering, frequently over the phone but can also be in person or <a href="https://searchunifiedcommunications.techtarget.com/definition/VoIP">VoIP</a> (i.e. Skype).</li><li><a href="https://searchmobilecomputing.techtarget.com/definition/SMiShing">Smishing</a> – Mobile phone-based text messaging (<a href="https://searchmobilecomputing.techtarget.com/definition/Short-Message-Service">SMS</a>) social engineering attacks</li><li>Thishing - Targeted phishing attacks… for example against senior management (<a href="https://searchsecurity.techtarget.com/definition/whaling">whaling</a> https://searchsecurity.techtarget.com/definition/whaling) and specific people/organisations (<a href="https://searchsecurity.techtarget.com/definition/spear-phishing">spear phishing</a> https://searchsecurity.techtarget.com/definition/spear-phishing) have recently become popular forms of social engineering attack for cyber-criminals.</li></ul><p>Vendors MUST, however, respond to this section of the requirements and articulate how their proposed solution explicitly protects from these styles of attacks and how other offerings are placed as part of their proposal for enablement etc. (including policy and training) collectively provide the required degree of protection and mitigation.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.17 Cloud Security Posture Management Requirements

<table data-header-hidden><thead><tr><th width="614"></th><th width="141"></th></tr></thead><tbody><tr><td><p><strong>5.17.1 Continuous Posture Assessment</strong></p><p>The project MUST deliver continuous cloud security posture assessments of cloud environments through security and compliance teams. The solution must be able to manage the massive number of security posture management issues that will confront the project as infrastructure is deployed on public clouds with even modest deployments.<br></p><p>The solution MUST be able to provide an assessment approach which addresses all of the common security concerns accompanying public cloud based deployments using containers, kubernetes and other public cloud services etc..</p><p>The key requirements are both taking control of; and keeping control of security risks in multiple, ever-growing and ever-changing cloud environments. Typically it is just too much data to process, too often, with an ever-expanding attack surface as more applications and services are deployed. This is the problem space that MUST be dealt with by the proposed solution and why continuous cloud security posture management is an absolute MUST for cloud deployments.<br></p><p>Note that GovStack may be deployed either on cloud infrastructure, on premise infrastructure or both. The intent of the CSPM requirements is for public cloud deployments although it can also be utilized for controlling on-premise public cloud offerings such as Azure Arc or AWS Outposts..</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.2 Inventory, Ownership and Customization</strong></p><p>In terms of the inventory of data and services deployed, the following MUST be able to be managed (see ensuing rows)</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.3 Inventory Collection Coverage</strong></p><p>Must collect the metadata from all available cloud resources that have been deployed and utilized in the account. This collection MUST go beyond the core types of services (compute, networking, database, and IAM etc.) to incorporate a complete security metadata view of the utilized cloud resources and any potential exposures both inside and outside containers.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.4 Data Ownership</strong></p><p>Solutions delivered as Software-as-a-Service (SaaS) provide quick onboarding, but they are typically managed by third-party with account-wide access to your cloud resources. This may present challenges with data ownership, compliance attestations of an external third party, and adherence to regional compliance mandates. These issues MUST be identified by CSPM.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.5 Customization</strong></p><p>3rd party solutions can vary widely in their ability to make adjustments to how data is collected, how security checks are implemented, how results are filtered/excluded and reported, and how and when teams are alerted for issues. Without full control over all aspects, you may end up with results and notifications that cannot be properly tuned, and this can lead to ignoring the tool and overall alert fatigue. The CSPM solution MUST provide the ability to navigate the posture across all 3rd party components and alleviate alert fatigue.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.6 Answer Complex/Advanced Questions</strong></p><p>Simple questions like “Is this S3 Bucket Public?” can usually be identified easily, but questions like “Are there any publicly accessible virtual machines with attached instance credentials that allow reading from S3 buckets tagged ‘sensitive’?”, “Which GKE Clusters have pods with access to escalate to ‘Project Owner’ via the attached Service Account? MUST be able to be answered by the CSPM solution”</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.7 Provide Continuous Results and Triage</strong></p><p>The CSPM solution MUST be designed with tunable results tracking and results triage workflows across multiple assessment intervals for continuous assessment as the total deployed solution evolves.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.8 Focus on both Hardening and Compliance</strong></p><p>Most security practitioners are aware of the differences between an environment that is only compliant with one that is compliant and also well hardened. Compliance is a key driver for obtaining project funding and being able to operate a business legally, but going no further than compliance still leaves you open to critical risks. The CSPM tools MUST cover both security best practices and compliance objectives equally.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.9 Compliance Objectives Driven Approach</strong></p><p>The solution MUST be able to associate controls with one or more compliance objectives. Views, filtering, and workflows should be driven by compliance objectives. For example, filtering controls by “PCI”, “NIST 800-53”, or “CIS” should narrow down the list to the controls that align with those frameworks with an identical mechanism that can also be used to filter controls for “lateral movement” or “privilege escalation”.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.17.10 CSPM Basics</strong></p><p>The CSPM solution MUST address the basic cloud security posture management abilities as defined above for the broadest range of public cloud infrastructure providers (for example AWS, GCP and Azure).</p><p>The following basic activities MUST be supported:</p><ol><li>Collect several types of public-cloud-specific configuration data on a one-time or recurring basis from any cloud account resources (VMs, Clusters, IAM, etc),</li><li>Parse and load the configuration data into a graph database with deep linked relationships between resources to support advanced querying capabilities,</li><li>Run a customizable series of policy checks to determine conformance and record passing/failing resources on a recurring basis on that configuration,</li><li>Create custom groupings of related policy checks aiding in tracking remediation efforts and an associated reduction in risk over time,</li><li>Provide notifications to multiple destinations (email, logs, instant message etc.) when specified deviations from desired baselines occur.</li></ol></td><td>REQUIRED</td></tr></tbody></table>

## 5.19 Vulnerability Management and Security Automation Requirements

<table data-header-hidden><thead><tr><th width="643"></th><th width="114"></th></tr></thead><tbody><tr><td><p><strong>5.19.1 Security Automation in General</strong></p><p>In general the vulnerability scanning requirements are covered in other sections of this document. The focus of this requirement is automation of vulnerability management to limit the window of vulnerability to be as short as possible once a vulnerability becomes known. The project MUST implement security automation which means automated patching and upgrades of the software and firmware in and around the applications and networking infrastructure to ensure that patches addressing security vulnerabilities are deployed consistently across all of the infrastructure.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.19.2 Repeatability for both Cloud and On-Premise Deployments</strong></p><p>The security automation solution MUST provide a clean, consistent, simple and repeatable means of configuration management, applications deployment and patching that is flexible enough to support the entire infrastructure including both on-premise and cloud based deployments. Typically this would be achieved with a playbook style approach where playbooks are built using a language such as YAML and applied consistently through an automated scripting approach.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.19.3 Agentless Orchestration and Provisioning</strong></p><p>The solution MUST provide orchestration, provisioning, module, plugin and inventory management support in order to be comprehensive for enterprise needs. Ideally the solution provided MUST be agentless and not require any additional software to be deployed on each node in the network.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.19.4 Consistent Configuration Management</strong></p><p>The solution MUST provide simple, reliable, and consistent configuration management capabilities. Must be able to be deployed quickly and simply with many out-of-the-box plugins for common technologies. Configurations MUST be simple data descriptions of infrastructure which are both readable by humans and parsable by machines.<br></p><p>The solution itself MUST be able to connect to remote nodes under administration via SSH (Secure Socket Shell) key for secure configuration. For example configurations MUST be able to be consistently applied to hosts via lists of IP addresses and apply playbooks to install the configuration update on all the nodes. Subsequently the playbook can be executed from a control machine to effect the update. Logs MUST be taken and reported on to ensure that centralized admin is aware of any failure and can address them manually if necessary</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.19.5 Orchestrated Workflows</strong></p><p>The offered solution MUST provide orchestration which involves bringing different elements together to run a whole operation. For example, with application deployment, you need to manage not just the front-end and backend services but the databases, networks and storage among other components. The orchestration solution MUST also ensure that all the tasks are handled in the proper order using automated workflows and provisioning etc.. Orchestations and playbooks MUST be reusable and repeatable tasks that can be applied time and again to the infrastructure based on parameters.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.19.6 Site-wide Security Policy Implementation</strong></p><p>The solution MUST have the ability to implement sitewide security policies (such as firewall rules or locking down users) which can be implemented along with other automated processes. MUST be able to configure the security details on the control machine and run the associated playbook to automatically update the remote hosts with those details. This means that security compliance should be simplified and easily implemented. An admin’s user ID and password MUST NOT be retrievable in plain text.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.20 Security Risk Profiling and Management Requirements

See the section of this document dealing with [OSINT tools](5-cross-cutting-requirements.md#docs-internal-guid-0e34003e-7fff-c036-360f-0684a1c5f326)

## 5.21 Intrusion Prevention and Detection Requirements

<table data-header-hidden><thead><tr><th width="640"></th><th width="116"></th></tr></thead><tbody><tr><td><p><strong>5.21.1 HIDS, SIM and SIEM with Real-Time Integrity Monitoring</strong></p><p>The solution for intrusion prevention and detection MUST combine HIDS monitoring features with Security Incident Management (SIM)/Security Information and Event Management (SIEM) features. MUST also be able to perform real-time file integrity monitoring, Windows registry monitoring, rootkit detection, real-time alerting, and active response.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.21.2 Multi-Platform Support</strong></p><p>The solution MUST be multi-platform and support deployment on Windows Server, and most modern Unix-like systems including Linux, FreeBSD, OpenBSD, and Solaris etc.. The reason for this is that it is yet to be determined exactly which O/S infrastructure will be required for the full GovStack solution and it will likely end up being a hybrid mix of various O/S platforms but predominantly Linux in containers.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.21.3 Centralized Management</strong></p><p>The intrusion prevention and detection software MUST consist of a central manager for monitoring and receiving information from agents (most likely agents are required - they are small programs installed on the systems to be monitored. Of course an agentless solution will be acceptable if it is feasible). The central manager MUST include storage of the file integrity checking databases, logs, events, and system auditing entries.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.21.4 Basic IDS Features</strong></p><p>The intrusion prevention and detection solution MUST minimally offer the following features:</p><ul><li>Log-based Intrusion Detection</li><li>Rootkit Detection</li><li>Malware Detection</li><li>Active Response</li><li>Compliance Auditing</li><li>File Integrity Monitoring</li><li>System Inventory</li></ul><p>Note that this is a very minimalist set of requirements and vendors may offer enterprise level open source subscriptions that offer more advanced features for intrusion prevention and detection which are AI/ML based for example. It is up to each vendor to articulate the value of what they are offering and why it is necessary.</p></td><td>REQUIRED</td></tr></tbody></table>

### 5.22 Open Source Intelligence Platform (OSINT) Requirements <a href="#docs-internal-guid-0e34003e-7fff-c036-360f-0684a1c5f326" id="docs-internal-guid-0e34003e-7fff-c036-360f-0684a1c5f326"></a>

<table data-header-hidden><thead><tr><th width="631"></th><th width="116"></th></tr></thead><tbody><tr><td><p><strong>5.22.1 General OSINT Requirements</strong></p><p>The project MUST provide OSINT tools with the following purposes and general requirements in focus (see ensuing rows):</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.22.2 Discovery of Public-Facing Assets</strong></p><p>The most common function of OSINT tools is helping IT teams discover public-facing assets and mapping what information each possesses that could contribute to a potential attack surface. This is public information about vulnerabilities in services and technologies that cyber-criminals can potentially use to gain access. In general, these tools don’t typically try to look for things like specific program vulnerabilities or perform penetration testing but may also incorporate these features.<br></p><p>The main purpose of OSINT tools is determining what information someone could publicly discover about the organization's assets without resorting to hacking and offer security professionals the opportunity to proactively address these vulnerabilities by reading the reports.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.22.3 Discover Relevant Information Outside the Organization</strong></p><p>A secondary function that some OSINT tools perform is looking for relevant information outside of an organization, such as in social media posts or information posted at specific domains and locations that might be outside of a tightly defined network. Organizations which have acquired a lot of diverse IT assets are excellent candidates for OSINT tools and we see that this has huge potential for GovStack. Given the extreme growth and popularity of social media, looking outside the organization perimeter for sensitive information is helpful for just about any group.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.22.4 Collate Discovered Information into Actionable Form</strong></p><p>Finally, some OSINT tools help to collate and group all the discovered information into useful and actionable intelligence. Running an OSINT scan for a large enterprise can yield hundreds of thousands of results, especially if both internal and external assets are included. Piecing all that data together and being able to deal with the most serious problems first can be extremely helpful. The solutions offered MAY also incorporate AI/ML and neural network based solutions for better discovery and automation of analytics etc.</p><p>The offered solution SHOULD deliver better alignment of the organization's ability to comply with standards such as PCIDSS, HIPAA and GDPR etc. Prospective vendors SHOULD articulate how their solution achieves this goal.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.22.5 Open Source Offering</strong></p><p>The offered solution MUST be based fully on open source components. The vendor may offer subscriptions for support so long as the offered solution does not require those subscriptions in order to deliver the core functionality specified in this document.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.23 Fraud Prevention, Detection and Management Requirements <a href="#docs-internal-guid-ff5d3833-7fff-a26b-0c65-f8f928472a22" id="docs-internal-guid-ff5d3833-7fff-a26b-0c65-f8f928472a22"></a>

<table data-header-hidden><thead><tr><th></th><th width="118"></th></tr></thead><tbody><tr><td><strong>Functional Requirement</strong></td><td><p><strong>Type (Must/</strong></p><p><strong>Should/</strong></p><p><strong>May)</strong></p></td></tr><tr><td><p><strong>5.23.1 Identify Fraudulent Purchases and Transactions</strong></p><p>The solution MUST provide the ability to identify potentially fraudulent purchases, transactions, or access. The solution MUST continuously examine user behavior, and analyse risk figures then identify any suspicious activity that may require intervention.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.2 General Features Required</strong></p><p>The solution MUST be able to check the potential of fraudulent actions by users both internal and external, ensuring that transactions are lawful and genuine. The solution MUST also protect the sensitive information of both organizations and citizens (also see data leakage prevention). The solution MUST meet the following general features requirements:</p><ul><li>AI/Deep Learning (Collaborative)</li><li>Analytics/Data Mining</li><li>Insider Threat Monitoring</li><li>Risk Assessment</li><li>Transaction Scoring</li><li>Intelligence Reporting</li><li>ID Analytics and Alerts</li><li>Real-Time Monitoring</li><li>Blacklisting</li><li>Investigator Notes</li><li>Transaction Approval</li><li>Custom Fraud Parameters</li><li>Unified Platform</li><li>Data Enrichment</li><li>Continuous Innovation</li><li>Visualize real-time data</li><li>Anomaly detection</li><li>Frictionless Commerce</li><li>Early Warning System</li></ul></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.3 Fraud Information Dashboard</strong></p><p>The solution MUST provide an information dashboard with data visualization of statistical information and alerts pertaining to fraud prevention and detection that need to be addressed with an assigned priority.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.4 Data Import from Many Sources</strong></p><p>The solution MUST provide the ability to import data sets from many applications and databases in order to perform analysis and provide fraud analysis and scoring information along with alerts on configurable events and thresholds.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.5 CRM Integration</strong></p><p>The solution MUST provide integration with common customer relationship management solutions that are likely to be deployed as part and parcel of GovStack or perhaps already existing in the government's target architecture.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.6 API for Data Integration</strong></p><p>The solution MUST provide an open API for the purposes of integrating data from unknown sources to be checked for fraudulent activity.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.23.7 AI/ML Based Capabilities</strong></p><p>Ideally the solution SHOULD incorporate advanced AI and ML capabilities for the purposes of detecting fraud with a combination of neural network, pattern recognition and data mining approaches to identify potentially fraudulent events based on advanced models and historical learning.</p></td><td>OPTIONAL</td></tr><tr><td><p><strong>5.23.8 Investigator Notes and Workflows</strong></p><p>The solution MUST provide investigator notes and workflow capabilities for investigating potentially fraudulent incidents and managing those incidents through to resolution.</p></td><td>REQUIRED</td></tr></tbody></table>

### 5.24 Security Incident Response and Management Requirements <a href="#docs-internal-guid-c235aa3f-7fff-9bd8-7175-90882d93554f" id="docs-internal-guid-c235aa3f-7fff-9bd8-7175-90882d93554f"></a>

<table data-header-hidden><thead><tr><th width="624"></th><th width="114"></th></tr></thead><tbody><tr><td><p><strong>5.24.1 General Incident Response Requirements</strong></p><p>The solution MUST provide an incident response and management system that implements the following general requirements as a fully integrated solution (referring to the other sections of this document):</p><ol><li><a href="https://www.cynet.com/incident-response/#phase-1">Preparation of systems and procedures</a></li><li><a href="https://www.cynet.com/incident-response/#phase-2">Identification of incidents</a></li><li><a href="https://www.cynet.com/incident-response/#phase-3">Containment of attackers and incident activity</a></li><li><a href="https://www.cynet.com/incident-response/#phase-4">Eradication of attackers and re-entry options</a></li><li><a href="https://www.cynet.com/incident-response/#phase-5">Recovery from incidents, including restoration of systems</a></li><li><a href="https://www.cynet.com/incident-response/#phase-6">Lessons learned and application of feedback to the next round of preparation</a></li></ol></td><td>REQUIRED</td></tr><tr><td><p><strong>5.24.2 Support for NIST and/OR SANS</strong></p><p>In general the NIST and/or SANS incident response frameworks SHOULD be followed and the tooling MUST facilitate this.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.24.3 Assessment and Review Facilities</strong></p><p>The solution MUST provide capabilities for reviewing and documenting existing security measures and policies to determine effectiveness as well as performing a risk assessment to determine which vulnerabilities currently exist and the priority of your assets in relation to them.<br></p><p>This Information is then applied to prioritizing responses for incident types and is also used to reconfigure systems to cover vulnerabilities and focus protection on high-priority assets. This phase is where you refine existing policies and procedures or write new ones if they are lacking. These procedures include documenting a communication plan and the assignment of roles and responsibilities during an incident.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.24.4 Tools to Support Detection and Identification</strong></p><p>The solution MUST support the use of the tools and procedures determined in the preparation phase and define the process and teams to work on detecting and identifying any suspicious activity. When an incident is detected, team members need to work to identify the nature of the attack, its source, and the goals of the attacker.<br></p><p>During identification, any evidence collected MUST be protected and retained for later in-depth analysis. Responders MUST document all steps taken and evidence found, including all details. The purpose of this is to more effectively prosecute if and when an attacker is identified.</p><p><strong>5.25.5 Support for Communications Planning</strong></p><p>After an incident is confirmed, communication plans MUST be initiated by the system. These plans MUST inform all concerned parties by workflow (i.e. security board members, stakeholders, authorities, legal counsel, and eventually users of the incident) advising which steps MUST be taken.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.24.6 Threat Containment and Elimination</strong></p><p>The solution and its processes MUST support the containment and elimination of threats. After an incident is identified, containment methods are determined and enacted.<br></p><p>Containment:</p><p>The goal is to advance to this stage as quickly as possible to minimize the amount of damage caused.</p><p>Containment MUST be able to be accomplished in sub-phases:</p><ul><li>Short term containment—immediate threats are isolated in place. For example, the area of your network that an attacker is currently in may be segmented off. Or, a server that is infected may be taken offline and traffic redirected to a failover.</li><li>Long term containment—additional access controls are applied to unaffected systems. Meanwhile, clean, patched versions of systems and resources are created and prepared for the recovery phase.</li></ul><p>Elimination:</p><p>During and after containment, the full extent of an attack MUST be made visible. Once teams are aware of all affected systems and resources, they can begin ejecting attackers and eliminating malware from systems. This phase continues until all traces of the attack are removed. In some cases, this may require taking systems off-line so assets can be replaced with clean versions in recovery. It is anticipated that security automation tools will play a key role in this phase and SHOULD be integrated with the solution for this purpose (see the section outlining security automation requirements)</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.24.7 Recovery, Restoration and Refinement</strong></p><p>The solution MUST support a recovery, restoration and refinement phase where recovery and restoration of damaged systems is achieved by bringing last-known-good versions online. Ideally, systems can be restored without loss of data but this isn’t always possible.<br></p><p>Teams MUST be able to determine when the last clean copy of data was created and restore from it. The recovery phase typically extends for a while as it also includes monitoring systems for a while after an incident to ensure that attackers don’t return.</p><p>Feedback and refinement MUST be enabled where lessons learned by your team's reviews along with the steps that were taken with a response. The team MUST be able to address what went well, what didn’t, and document a process for future improvements.</p><p>Note that this is not something that gets performed in isolation by the incident response system but an integrated process that coordinates these phases across all security systems to formulate and execute the response.</p></td><td><br><br><br><br><br><br>REQUIRED<br><br><br><br><br><br><br><br><br><br><br><br></td></tr></tbody></table>

## 5.25 Security Testing and Sandbox Requirements <a href="#docs-internal-guid-e353cf30-7fff-1e04-763a-a981b6e132db" id="docs-internal-guid-e353cf30-7fff-1e04-763a-a981b6e132db"></a>

<table data-header-hidden><thead><tr><th width="626"></th><th width="119"></th></tr></thead><tbody><tr><td><p><strong>5.25.1 Comprehensive Sandbox</strong></p><p>The proposed solution MUST include a security sandbox environment with instances of the entire software stack and all of the security tools installed and configured such that security testing and scenarios can be addressed on an ongoing basis. This is not so much a solution requirement as a deployment requirement and MUST address all of the processes associated with each of the facets of security defined herein.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.25.2 Scalability</strong></p><p>The security sandbox environment MUST scale to a level that is suitable for testing scenarios such as DDOS prevention etc. but does not have to be implemented at the same scale as the regular test environment or the production environment for example.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.25.3 Test Scripting and Automation</strong></p><p>The project MUST conduct security testing using automated scripts as much as possible on an ongoing basis and the security team MUST take ownership of the ongoing securitization of all digital assets for each and every deployment. Note that the responsibility for these activities may ultimately be delegated to a government or country team in the case of build-X-transfer implementation scenarios. The role of the solution provider is to ensure that the baseline for these processes is established prior to any handover/transfer.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.26 Critical Digital Infrastructure Business Continuity Requirements <a href="#docs-internal-guid-881f626a-7fff-3f9d-90eb-ce39f1500b76" id="docs-internal-guid-881f626a-7fff-3f9d-90eb-ce39f1500b76"></a>

<table data-header-hidden><thead><tr><th width="634"></th><th width="117"></th></tr></thead><tbody><tr><td><p><strong>5.26.1 General Recovery Requirements</strong></p><p>The solution MUST cater for the recovery of all critical digital infrastructure in the case of major security incidents. Refer to the section above regarding the indecent response system for the general requirements regarding how such recovery MUST be performed.</p></td><td>REQUIRED</td></tr><tr><td><p><strong>5.26.2 Backup for Code and Images</strong></p><p>The backup and recovery systems for code, system images and data MUST cater for complete recovery of all critical digital infrastructure after natural disasters and also security incidents. The detailed requirements for such recovery of systems are to be provided by each building block as custodian of the code, images and data. Detailed information on the specific recovery requirements MUST be provided by the project for each GovStack implementation as they may vary widely due to constraints on budget and capabilities.</p></td><td>REQUIRED</td></tr></tbody></table>

## 5.27 Data Structures <a href="#docs-internal-guid-0847c8be-7fff-8ca0-51c8-6bbba084e43f" id="docs-internal-guid-0847c8be-7fff-8ca0-51c8-6bbba084e43f"></a>

### 5.27.1 Resource Model

The resource model shows the relationship between data objects that are used by this Building Block. The following resource model depicts the basic elements of identity and access management (IAM) solutions required organized into domains:

![](../@site/static/img/image1.png)

### 5.27.2 Data Elements <a href="#docs-internal-guid-396d89e5-7fff-e3e8-ad44-66086dd2bb92" id="docs-internal-guid-396d89e5-7fff-e3e8-ad44-66086dd2bb92"></a>

The data elements provide detail for the resource model defined above. This section will list the core/required fields for each resource. Note that the data elements can be extended for a particular use case, but they must always contain at least the fields defined here. Information about data elements will include:

* Name
* Description
* Data Type
* Required/Optional flag
* Link to applicable standard(s)
* Notes

### 5.27.3 Example REST Authentication API

The following is a minimal example of how OpenIAM implements REST based authentication using its REST API:

(Note: The APIs will need to include appropriate request and response version numbers, for example, see [https://docs.google.com/document/d/12b696fHlOAAHygFF5-XxUJkFyFjMIV99VDKZTXnnAkg/edit#heading=h.h9ypjkyetr1i](https://docs.google.com/document/d/12b696fHlOAAHygFF5-XxUJkFyFjMIV99VDKZTXnnAkg/edit#heading=h.h9ypjkyetr1i))

**URL**

/idp/rest/api/v1/auth/public/login

**Method**

POST

**Request Parameters**

* login: user login (optional)
* password: user password (optional)
* postbackURL: redirectURL after success login (optional)

**Headers**

Content-Type:application/x-www-form-urlencoded

**cURL Example**

curl 'http://127.0.0.1:8080/idp/rest/api/auth/public/login' -X POST --data 'login=admin\&password=pass123456'

**Success Response Example**

```
{
  "primaryKey": null,
  "status": 200,
  "errorList": null,
  "redirectURL": "/selfservice",
  "successToken": null,
  "successMessage": null,
  "contextValues": null,
  "possibleErrors": null,
  "passwordExpired": false,
  "userId": "3000",
  "unlockURL": null,
  "tokenInfo": {
    "authToken": "+Y9NkOrjOWn0BehKr6Cg1F7KcFIiY=",
    "timeToLiveSeconds": -1
  },
  "error": false
}
```

**Error Response Example**

```
{
  "primaryKey": null,
  "status": 500,
  "errorList": [
    {
      "i18nError": null,
      "error": "INVALID_LOGIN",
      "validationError": null,
      "params": null,
      "message": "Invalid Login and/or Password"
    }
  ],
  "redirectURL": null,
  "successToken": null,
  "successMessage": null,
  "contextValues": null,
  "possibleErrors": null,
  "passwordExpired": false,
  "userId": null,
  "unlockURL": null,
  "tokenInfo": null,
  "error": true
}
```

### **5**.27.4 Example OAuth2 Authentication API <a href="#docs-internal-guid-95b38c92-7fff-abfc-b395-b64d56ed6c74" id="docs-internal-guid-95b38c92-7fff-abfc-b395-b64d56ed6c74"></a>

The following is a minimal example of how OpenIAM implements authentication with OAuth2 by requesting an OAuth2 token:

**URL**

/idp/oauth2/token

**Method**

POST

**Request Parameters**

* **client\_secret**: Value of the client secret from OAuth client configuration page
* **client\_id**: Value of the client ID from OAuth client configuration page
* **grant\_type**: Type of grant flow
* **username**: Login of requester
* **password**: Password of requester

**Headers**

Content-Type:application/x-www-form-urlencoded

**cURL Example**

```
curl -v -XPOST --data 
'client_secret=AAAAA&client_id=BBBBB&grant_type=password&username=DDDD&password=EEEE' 'http://127.0.0.1:8080/idp/oauth2/token'
Success Response Example
{
"access_token": "ffj9Ub4lP-2_W4kXAXJ9MsleMxdDi9ALo0JqQw.3hV4driKa4IWXOSJ42PEQadFpN2FnpRruFLWD3",
"token_type": "Bearer",
"expires_in": 1320,
"refresh_token": "3nlth7DevrnjjpebATKkYCirs2aiy6L6SsBF_cpyxSXgVliwXC1rsCxRg99LCr7gHgYJ.A.VU"
}
```

**Error Response Example**

```
{
"error": "unauthorized_client",
"error_description": "Missing required parameter: client_id or client application is not registered"
}
```

### **5**.27.5 Example OAuth2 Token Renewal API <a href="#docs-internal-guid-db53651e-7fff-5d94-fd83-af45de38b538" id="docs-internal-guid-db53651e-7fff-5d94-fd83-af45de38b538"></a>

The following is a minimal example of how OpenIAM implements authentication token renewal:

**URL**

/idp/rest/api/auth/renewToken

**Method**

GET

**Headers**

* Authorization: with oAuth token in format 'Bearer: \<token>'
* Cookie: with current valid authentication token in format 'OPENIAM\_AUTH\_TOKEN=\<token>'

**cURL Example**

```
// Scurl -XGET -v -H 'Authorization: Bearer ssssss' -H 'Cookie: OPENIAM_AUTH_TOKEN=asdasdas' 'http://127.0.0.1:8080/idp/rest/api/auth/renewToken'
```

**Success Response Example**

```
{
"authToken": "asdas+asd/YagqkcJEql+asd=",
"timeToLiveSeconds": -1
}
```

**Error Response Example**

### **5**.27.6 Example OAuth2 Authorization API <a href="#docs-internal-guid-f9280876-7fff-8c97-e507-a5f8bb1d38c8" id="docs-internal-guid-f9280876-7fff-8c97-e507-a5f8bb1d38c8"></a>

The following is a minimal example of how OpenIAM implements authorization using OAuth2:

**URL**

{server\_url}/idp/oauth2/token/authorize

Replace {server\_url} with the name of the server.

**Method**

GET

**Parameters**

* response\_type: codetoken
* client\_id: webconsole/Access Control/Authentication Providers/\*needed provider\* edit/ Client ID field
* redirect\_uri: webconsole/Access Control/Authentication Providers/\*needed provider\* / Redirect Url. Use 'Space' or 'Enter' to separate values field.

**cURL Example**

curl

<mark style="color:green;">'http://dev1.openiamdemo.com:8080/idp/oauth2/authorize?response\_type=code\&client\_id=EF4128DCC0D24ED3BAC17FC918FDDBF5\&redirect\_uri=http://dev1.openiamdemo.com:8080/oauthhandler'</mark>

or, just:

curl

<mark style="color:green;">'http://dev1.openiamdemo.com:8080/idp/oauth2/authorize?response\_type=code\&client\_id=EF4128DCC0D24ED3BAC17FC918FDDBF5\&redirect\_uri=http://dev1.openiamdemo.com:8080/oauthhandler'</mark>

**Success Response Example**

redirect to redirect\_uri?code=code

**Error Response Example**

redirect to redirect\_uri <mark style="color:purple;">with</mark> error

### 5.27.7 Example OAuth2 Authorization Implicit Grant Flow API <a href="#docs-internal-guid-e8f5c441-7fff-e0c4-8bdf-c4757093ffdf" id="docs-internal-guid-e8f5c441-7fff-e0c4-8bdf-c4757093ffdf"></a>

The following is a minimal example of how OpenIAM implements an implicit grant flow API style of authentication:

**URL**

{server\_url}/idp/oauth2/token/authorize

Replace {server\_url} with the name of the server.

**Method**

GET

**Parameters**

* response\_type: token
* client\_id: webconsole/Access Control/Authentification Providers/\*needed provider\* edit/ Client ID field
* redirect\_uri: webconsole/Access Control/Authentification Providers/\*needed provider\* / Redirect Url. Use 'Space' or 'Enter' to separate values field.

**cURL Example**

curl -v XGET 'http://dev1.openiamdemo.com:8080/idp/oauth2/authorize?response\_type=token\&client\_id=EF4128DCC0D24ED3BAC17FC918FDDBF5\&redirect\_uri=http://dev1.openiamdemo.com:8080/oauthhandler'

or, just:

curl 'http://dev1.openiamdemo.com:8080/idp/oauth2/authorize?response\_type=token\&client\_id=EF4128DCC0D24ED3BAC17FC918FDDBF5\&redirect\_uri=http://dev1.openiamdemo.com:8080/oauthhandler'

**Success Response Example**

redirect to redirect\_uri?code=access\_token=Pcej-9OdU\_wshAjTn76MP-Cj5OgY\_sfdYrt\&expires\_in=60000\&token\_type=Bearer

**Error Response Example**

redirect to redirect\_uri with error

### 5.27.8 Example Get OAuth2 Token Information API <a href="#docs-internal-guid-96ade525-7fff-a23e-0f0d-df99d093f571" id="docs-internal-guid-96ade525-7fff-a23e-0f0d-df99d093f571"></a>

The following is a minimal example of how OpenIAM implements a get operation for token information:

**URL**

{server\_url}/idp/oauth2/token/info

Replace {server\_url} with the name of the server.

**Method**

GET

**Parameters**

token: token should be created via [Create token](https://docs.openiam.com/docs-5.1.14/html/API/RESTful/oauth-request.htm?tocpath=API%20Guide%7CPart%20I%3A%20RESTful%20web%20services%20API%7C5.%20OAuth%20request%20list%7C\_\_\_\_\_0#token-create).

**cURL Example**

curl -v XGET

'http://dev1.openiamdemo.com:8080/idp/oauth2/token/info?token=rdSOyor6hqJ2CrQ5QrpeXgX.ItgVEx1.nskN'

or, just:

curl

'http://dev1.openiamdemo.com:8080/idp/oauth2/token/info?token=rdSOyor6hqJ2CrQ5QrpeXgX.ItgVEx1.nskN'

**Success Response Example**

```
{
"expired": false,
"client_id": "92BF26DD50D748668730F7639C4A0D3D",
"user_id": "3000",
"access_token": "Lf_Sc-YeKHB8rsGfiGcLMKJOxbTGmpbdYs5wK3i7ZhINrjJlTOHEuV-phwJ1wE7.MjWqDcx8Lpri",
"expires_in": 1709,
"expires_on": 1531332707193,
"scopes": [
{
"scopeId": "c42a190a6488010b01648810b83a005a",
"name": "dev1 - /idp/oauth2/token/info"

},
{
"scopeId": "c42a190a6488010b01648810bdfd0096",
"name": "dev1 - /idp/rest/api/*"
},
{
"scopeId": "c42a190a6488010b01648810be2a0098",
"name": "dev1 - /webconsole/rest/api/*"
},
{
"scopeId": "c42a190a6488010b01648810be6d009b",
"name": "dev1 - /selfservice/rest/api/*"
},
{
"scopeId": "c42a190a6488010b01648810be96009d",
"name": "dev1 - /selfservice-ext/rest/api/*"
},
{
"scopeId": "c42a190a6488010b01648810bebf009f",
"name": "dev1 - /webconsole-idm/rest/api/*"
}
]
}
```

**Error response example**

```
// Some code{"code":401,"error":"invalid_token","error_description":"Authorization token is expired"}
```

### 5.27.9 Example Create OAuth2 Token API <a href="#docs-internal-guid-08a8d5a5-7fff-357c-48b1-1b67f9930232" id="docs-internal-guid-08a8d5a5-7fff-357c-48b1-1b67f9930232"></a>

The following is a minimal example of how OpenIAM would create an OAuth2 token using authorization grant flow style:

**URL**

{server\_url}/idp/oauth2/token

Replace {server\_url} with the name of the server.

**Method**

POST

**Parameters**

* **client\_secret**: webconsole/Access Control/Authentification Providers/\*needed provider\* edit/ Client Secret field
* **client\_id**: webconsole/Access Control/Authentification Providers/\*needed provider\* edit/ Client ID field
* **grant\_type**: authorization\_code
* **redirect\_uri**: webconsole/Access Control/Authentification Providers/\*needed provider\* / Redirect Url. Use 'Space' or 'Enter' to separate values field
* **code**: code should be generated with [Authorization code grant flow](https://docs.openiam.com/docs-5.1.14/html/API/RESTful/oauth-request.htm?tocpath=API%20Guide%7CPart%20I%3A%20RESTful%20web%20services%20API%7C5.%20OAuth%20request%20list%7C\_\_\_\_\_0#auth-code-grant) request.

Headers

Content-Type: application/x-www-form-urlencoded

**cURL Example**

curl -v -XPOST --data 'client\_secret=client\_secret\&client\_id=client\_id\&grant\_type=authorization\_code\&redirect\_uri=redirect\_uri\&code=code' 'http://dev1.openiamdemo.com:8080/idp/oauth2/token'

**Success Response Example**

```
{
"access_token": "MjwOxreF7e-NW_NBA6UNuB9d_4IcohdK2bUSxqZ_BxDlCG7uD.ZstmoKwvuWq1hL49pClk3dlo",
"token_type": "Bearer",
"expires_in": 1800
}
```

**Error Response Example**

```
{
"error": "invalid_request",
"error_description": "Code parameter is expired"
}
```

```
{
"error": "invalid_request",
"error_description": "Redirect URL does not mach to initial one."
}
```

#### **5**.27.10 Example Revoke OAuth2 Token API <a href="#docs-internal-guid-33fc6069-7fff-18a1-0bb2-acf18712212b" id="docs-internal-guid-33fc6069-7fff-18a1-0bb2-acf18712212b"></a>

The following is a minimal example of how OpenIAM implements OAuth2 token revocation:

**URL**

{server\_url}/idp/oauth2/token/revoke

Replace {server\_url} with the name of the server.

**Method**

POST

**Headers**

Content-Type=application/x-www-form-urlencoded

**Parameters**

token: token should be created via [Create token](https://docs.openiam.com/docs-5.1.14/html/API/RESTful/oauth-request.htm?tocpath=API%20Guide%7CPart%20I%3A%20RESTful%20web%20services%20API%7C5.%20OAuth%20request%20list%7C\_\_\_\_\_0#token-create).

**cURL Example**

curl -v XPOST --data 'token=token' 'http://dev1.openiamdemo.com:8080/idp/oauth2/revoke'

**Success Response Example**

```
{
"status": "SUCCESS",
"errorCode": null,
"errorText": null,
"fieldMappings": null,
"stacktraceText": null,
"responseValue": null,
"errorTokenList": null,
"failure": false,
"success": true
}
```

**Error Response Example**

```
{"code":403,"error":"insufficient_scope","error_description":"The request requires higher privileges than provided by the access token","scope":"1531291154553_/idp/oauth2/revoke"}
```

### \*\*5.\*\*27.11 Example Validate OAuth2 Token API <a href="#docs-internal-guid-fa87f843-7fff-24b8-8635-6d6007cd45d1" id="docs-internal-guid-fa87f843-7fff-24b8-8635-6d6007cd45d1"></a>

The following is a minimal example of how OpenIAM implmenents OAuth2 token validation:

**URL**

{server\_url}/idp/oauth2/token/validate

Replace {server\_url} with the name of the server.

**Method**

GET

**Parameters**

token: token should be created via [Create token](https://docs.openiam.com/docs-5.1.14/html/API/RESTful/oauth-request.htm?tocpath=API%20Guide%7CPart%20I%3A%20RESTful%20web%20services%20API%7C5.%20OAuth%20request%20list%7C\_\_\_\_\_0#token-create).

**cURL Example**

curl -v XPOST --data 'refreesh\_token=refreesh\_token' 'http://dev1.openiamdemo.com:8080/idp/oauth2/token/refresh'

**Success Response Example**

```
{
"access_token": "j4I6p0vDxZKduJXlipXZq5LNQqY1aJWvtYp812.k6246Sn2FY3rpyos..qJtScD8.wjytm1idsnopHmb.u",
"token_type": "Bearer",
"expires_in": 60,
"refresh_token": "0q1V8ZJaayxV5qcD4JtwF5.LyQOPMaZY.cNsIuZAYQ-TXGqrZDpy6AEOhc58dwEjgHDN2Bx_J.XkVTZ"
}
```

**Error response example**

```
{
"timestamp": 1531449532875,
"status": 400,
"error": "Bad Request",
"exception": "org.springframework.web.bind.MissingServletRequestParameterException",
"message": "Required String parameter 'refresh_token' is not present",
"path": "/idp/oauth2/token/refresh"
}
```

### **5**.27.13 Example User Information from OAuth2 Token API <a href="#docs-internal-guid-c2915b28-7fff-7927-5fc7-0a2074dd1a96" id="docs-internal-guid-c2915b28-7fff-7927-5fc7-0a2074dd1a96"></a>

The following is a minimal example of how user information can be obtained from OpenIAM using an OAuth2 token:

**URL**

{server\_url}/idp/oauth2/userinfo

Replace {server\_url} with the name of the server.

**Method**

GET

**Parameters**

token: token should be created via [Create token](https://docs.openiam.com/docs-5.1.14/html/API/RESTful/oauth-request.htm?tocpath=API%20Guide%7CPart%20I%3A%20RESTful%20web%20services%20API%7C5.%20OAuth%20request%20list%7C\_\_\_\_\_0#token-create).

**cURL Example**

curl -v XGET 'http://dev1.openiamdemo.com:8080/idp/oauth2/userinfo?token=rdSOyor6hqJ2CrQ5QrpeXgX.ItgVEx1.nskN'

or, just:

curl 'http://dev1.openiamdemo.com:8080/idp/oauth2/userinfo?token=rdSOyor6hqJ2CrQ5QrpeXgX.ItgVEx1.nskN'

**Success Response Example**

```
{
"sub": "3000"
}
```

**Error Response Example**

```
{"code":401,"error":"invalid_request","error_description":"Authorization token is not found"}
{"code":403,"error":"insufficient_scope","error_description":"The request requires higher privileges than provided by the access token","scope":"1531291154428_/idp/oauth2/userinfo"}
```

### **4**.27.14 Example API for Defining Resources, Roles, Access and Provisioning <a href="#docs-internal-guid-8c9caf33-7fff-a90a-d642-5ff061f58564" id="docs-internal-guid-8c9caf33-7fff-a90a-d642-5ff061f58564"></a>

The most comprehensive API available for this is delivered by OpenIAM. Unfortunately this API is currently delivered in SOAP. The purpose of this API is to provide 3rd parties the ability to create resources, roles and access within the IAM system. There are multiple options to get this done including batch upload and configuration using the administrative user interface. This would need to be addressed at implementation time using the most practical means. There does not seem to be a current use case for the BB’s to create these types of resources on the fly using the IAM API. The API definitions can be found here: [https://docs.openiam.com/docs-5.1.14/html/docs.htm#API/SOAP/SOAP.htm%3FTocPath%3DAPI%2520Guide%7CPart%2520II%253A%2520SOAP%2520API%2520integration%2520services%7C\_\_\_\_\_0](https://docs.openiam.com/docs-5.1.14/html/docs.htm#API/SOAP/SOAP.htm%3FTocPath%3DAPI%2520Guide%7CPart%2520II%253A%2520SOAP%2520API%2520integration%2520services%7C\_\_\_\_\_0)
