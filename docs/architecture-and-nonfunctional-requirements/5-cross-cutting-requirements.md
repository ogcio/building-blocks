# 5 Cross-Cutting Requirements

Building blocks are responsible for meeting all cross-cutting requirements or specifying why specific requirements do not apply. Govstack compliance and certification processes will validate these requirements.

## 5.1 Follow TM Forum Specification REST API Design Guidelines Part 1 (REQUIRED) <a href="#_wyofs1ddrlgk" id="_wyofs1ddrlgk"></a>

See: [TM Forum REST API Design Guidelines](https://www.tmforum.org/resources/specification/tmf630-rest-api-design-guidelines-4-2-0/)

Some key principles from these design guidelines are as follows:

* APIs MUST not include Personally Identifiable Information (PII) or session keys in URLs - use POST or other methods for this
* MUST support caching/retries
* Resource identification in requests Individual resources are identified in requests, for example using [URIs ](https://en.wikipedia.org/wiki/Uniform\_resource\_identifier)in RESTful Web services. The resources themselves are conceptually separate from the representations that are returned to the client. For example, the server could send data from its database as [HTML](https://en.wikipedia.org/wiki/HTML), [XML ](https://en.wikipedia.org/wiki/XML)or as [JSON](https://en.wikipedia.org/wiki/JSON)—none of which are the server's internal representation.
* Resource manipulation through representations. When a client holds a representation of a resource, including any [metadata ](https://en.wikipedia.org/wiki/Metadata)attached, it has enough information to modify or delete the resource's state.
* Self-descriptive messages Each message includes enough information to describe how to process the message. For example, which parser to invoke can be specified by a [media type](https://en.wikipedia.org/wiki/Media\_type).

## 5.2 Follow TM Forum Specification REST API Design Guidelines Parts 2-7 (RECOMMENDED) <a href="#_19suuzwtdje" id="_19suuzwtdje"></a>

See: [TM Forum REST API Design Guidelines](https://www.tmforum.org/resources/specification/tmf630-rest-api-design-guidelines-4-2-0/)

## 5.3 Communicate with other BBs only via API (REQUIRED)

Paraphrased from the Amazon API Mandate: [https://api-university.com/blog/the-api-mandate/](https://api-university.com/blog/the-api-mandate/)

1. All BBs must expose their data and functionality through service interfaces (APIs).
2. Building Blocks communicate with each other through these interfaces.
3. There will be no other form of interprocess communication allowed: no direct linking, no direct reads of another team’s data store, no shared-memory model, no back-doors whatsoever. The only communication allowed is via service interface calls over the network.
4. It doesn’t matter what technology is used. HTTP, Corba, Pubsub, custom protocols — doesn’t matter.
5. All service interfaces, without exception, must be designed from the ground up to be externalizable. That is to say, the team must plan and design to be able to expose the interface to developers in the outside world. No exceptions.

Building blocks MUST NOT use shared databases, file systems or memory for data exchange with other building blocks.

## 5.4 APIs must be Versioned (REQUIRED)

Use semantic versioning when documenting changes to API definitions. Any breaking changes to APIs MUST use a different endpoint, as shown here: e.g. /api/v1 and /api/v2

See [https://semver.org/](https://semver.org/)

## 5.5 Documentation must be Provided (REQUIRED)

Documentation on the installation and use of the Building Block MUST be provided. Where possible, this documentation SHOULD be stored alongside code in a repository. Documentation MAY be generated from code where applicable.

## 5.6 Provide an OpenAPI specification (REQUIRED)

Each building block’s service APIs MUST be defined and exposed using a standardized machine-readable language. External APIs are described using the OpenAPI 3.x specification. See the following resources for additional information:

* [Definition of the OpenAPI standard ](https://swagger.io/docs/specification/about/)
* [Swagger OpenAPI 3.0 Specification ](https://github.com/OAI/OpenAPI-Specification/blob/main/versions/3.0.3.md)

## 5.7 Building blocks must be deployable as a container (REQUIRED)

* Each building block MUST be ready to be deployed as independent container images. Source code and build instructions SHOULD be committed to a public code repository where possible.
* A building block may be composed with Kubernetes or docker compose. All build files must be included alongside the source code.

## 5.8 Include all deployment scripts (RECOMMENDED)

When a building block requires deployment tools such as Kubernetes or Ansible, configuration and deployment scripts should be included in the building block repository. Use of this type of deployment configuration will make individual components of the building block independently scalable and make building blocks less monolithic and more efficient.

## 5.9 Comply with GDPR Principles (REQUIRED)

Building Blocks MUST conform to GDPR principles, including the right to be forgotten account deletion, and privacy requirements to protect the rights of individuals. Note that these requirements may vary by region, and building blocks must conform to regulatory requirements wherever they are deployed.

## 5.10 Include Support for Capturing Logging information (REQUIRED)

Building Blocks MUST have a mechanism for generating logging information. This may be as simple as using STDOUT and capturing through docker logs, or may use other log sinking technologies.

## 5.11 Use Web Hooks for Callbacks (REQUIRED)

When Building Blocks require callback functionality, they must use webhooks and not direct links to functions within the building block.

## 5.12 Enforce Transport Security (REQUIRED)

All Building Blocks MUST support secure HTTPS transport with TLS 1.3 and insecure cyphers disabled.

## 5.13 GET and PUT APIs must be Idempotent (REQUIRED)

GET and PUT APIs (as well as HEAD, OPTIONS, and TRACE) must be idempotent, returning the same value if called multiple times. POST and DELETE APIs will not be idempotent as they change the underlying data. Reference [https://restfulapi.net/idempotent-rest-apis/](https://restfulapi.net/idempotent-rest-apis/) for more information.

## 5.14 Use Stateless APIs wherever Possible to Enhance Scalability (RECOMMENDED)

API calls SHOULD be able to be made independently of one another. Each API call should contains all of the data necessary to complete itself successfully.

## 5.15 Include Transaction/Trace/Correlation IDs (RECOMMENDED)

Transactions that cross multiple services SHOULD provide a correlation ID that is passed with every request and response. This allows for easier tracing and tracking of a specific transaction.

## 5.16 Include Clearly-Defined Key Rotation Policies (RECOMMENDED)

Some blocks may require the use of security keys. Those that do must have clearly defined key rotation policies to enhance security

## 5.17 Databases should not Include Business Logic (RECOMMENDED)

Database processing tools like triggers and stored procedures should be avoided.

## 5.18 Use only Unicode for Text (REQUIRED)

## 5.19 Use ISO8601/UTC for Timestamps (REQUIRED)

## 5.20 Building Blocks must be Autonomous (REQUIRED)

Each building block MUST be capable of running independently, without requiring other dependencies such as external data stores or other building blocks.

## 5.21 Use Secure Configuration (REQUIRED)

Configuration MUST be done using secure processes, such as environment variables or a secure secret store.

## 5.22 Design for Asynchronous First (RECOMMENDED)

Designs should support occasional connectivity/low bandwidth, and should allow for asynchronous communication between building blocks. A Publish/Subscribe design pattern can be used to handle changes, allowing loosely-coupled solutions to be assembled without changing existing APIs.

## 5.23 Use Standardized Data Formats for Interchange (REQUIRED)

JSON SHOULD be used for data models/services wherever possible. See [https://www.json.org/json-en.html](https://www.json.org/json-en.html). Where JSON exhange is not possible, building blocks must use other standard data formats (such as XML).

## 5.24 Use Existing Standards for Data Interchange, Where Available (RECOMMENDED)

If an existing standard is available, it should be used, e.g. DICOM/Hl7/FHIR for healthcare. TMForum has a large library of standardized APIs and data models that can be used.

Building blocks and building block solutions MUST leverage existing standards, especially those listed in the [Standards section](7-standards.md) below.

## 5.25 Use I/O Sanitization (RECOMMENDED)

Building blocks SHOULD validate all incoming data to ensure that it conforms with the expected format and type. APIs should also sanitize incoming data, removing any unsafe characters or tokens.

## 5.26 Provide a Compliance Test Mock/Example Implementation (OPTIONAL)

A building block MAY provide a mock testing implementation of API functionality to show example endpoints and data payloads. See [https://github.com/GovStackWorkingGroup/bb-template/tree/main/examples](https://github.com/GovStackWorkingGroup/bb-template/tree/main/examples) for additional information.

## 5.27 Building blocks should be Localizable (RECOMMENDED)

Where a building block has a human user interaction, it SHOULD be able to present information to the user in their local language. Building blocks should be designed to support multiple locales.

## 5.28 Use NTP Synchronization (RECOMMENDED)

Where precise timestamps are required, building blocks SHOULD leverage Network Time Protocol (NTP) to synchronize timestamps between servers.

## Other Considerations

Software development best practices are recommended for all building blocks. The following guidelines should be followed as part of the software development process.

### EOL SHOULD be at Least 5 Years <a href="#_fo8til974qj2" id="_fo8til974qj2"></a>

No languages, frameworks, or dependencies should be used in a building block where that component has an EOL of less than 5 years.

### Preference for TIOBE Top 25 Languages

See [https://www.tiobe.com/tiobe-index/](https://www.tiobe.com/tiobe-index/)

Where possible, building blocks SHOULD be written using commonly used languages to ensure ongoing maintenance and support are as easy as possible. Building blocks MAY leverage less common languages, such as shell scripting where needed.

### Regular Security and Code Quality Audits SHOULD be Run

These should be run across the code base and dependencies, e.g. [https://www.sonarqube.org/](https://www.sonarqube.org) and/or [https://snyk.io/](https://snyk.io) .

### SHOULD Include Unit and Integration Test Coverage

Building blocks should include tests that provide both unit and integration test coverage

### SHOULD Follow Best Practices for Public Code

See [https://standard.publiccode.net/](https://standard.publiccode.net) and practices outlined here:

* [Code in the Open](https://standard.publiccode.net/criteria/code-in-the-open.html)
* [Bundle Policy and Source Code](https://standard.publiccode.net/criteria/bundle-policy-and-code.html)
* [Create Reusable and Portable Code](https://standard.publiccode.net/criteria/reusable-and-portable-codebases.html)
* [Welcome Contributions](https://standard.publiccode.net/criteria/open-to-contributions.html)
* [Maintain Version Control](https://standard.publiccode.net/criteria/version-control-and-history.html)
* [Require Review of Contributions](https://standard.publiccode.net/criteria/require-review.html)
* [Document Your Objectives](https://standard.publiccode.net/criteria/document-objectives.html)
* [Document your code](https://standard.publiccode.net/criteria/documenting.html)
* [Use plain English](https://standard.publiccode.net/criteria/understandable-english-first.html)
* [Use open standards](https://standard.publiccode.net/criteria/open-standards.html)
* [Use continuous integration](https://standard.publiccode.net/criteria/continuous-integration.html)
* [Publish with an open license](https://standard.publiccode.net/criteria/open-licenses.html)
* [Use a coherent style](https://standard.publiccode.net/criteria/style.html)
* [Pay attention to codebase maturity](https://standard.publiccode.net/criteria/advertise-maturity.html)
