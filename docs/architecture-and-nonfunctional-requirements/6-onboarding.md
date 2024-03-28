# 6 Onboarding Products

It is vital that GovStack be able to connect to existing applications. Likewise, existing applications should be able to connect to and utilize GovStack resources as they see fit. This must be done without compromising the easy and secure interoperability provided by the GovStack system.

GovStack has defined a process for an existing product to become compliant with GovStack. This process is outlined in [this document](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/76906515/Compliance+Concept). Note that there are various levels of compliance that are defined. Any product owners or maintainers that are interested in the compliance process can use the GovStack testing platform to begin: [https://testing.govstack.global](https://testing.govstack.global)

This section contains resources can be used by existing platforms to integrate into the GovStack ecosystem. The first section describes 'Adaptors' which can be used to translate an existing API into a GovStack-conformant API. The second section describes Native GovStack implementation. Finally we describe the GovStack Testing Harness which allows products to run automated tests that have been developed by the GovStack team to determine how closely an application conforms to the specifications and expected behaviors described by the Building Block specifications.

### 6.1 Adaptors

Adaptors are used to map existing APIs and functionality in a Digital Public Good into a format and scheme that is compatible with the GovStack API specifications.

Adaptors may transform data formats (ie. XML to json), may transform URLs/protocols, or may be used to map GovStack APIs and data structures into sector-specific standards (ie. FHIR patient records).

#### 6.1.1 Key Components and Definitions <a href="#key-components-and-definitions" id="key-components-and-definitions"></a>

**Adaptor:** An adaptor provides both URL and payload mapping between an existing API developed by a DPG and the GovStack API definitions for the Building Block that the DPG provides functionality for.

**Workflow:** The workflow Building Block is used to manage more complex transactions where multiple Building Blocks must be called to complete a request (multi-part requests) or where retry/rollback/compensating transactions must be implemented.

**Information Mediator:** The Information Mediator is used transfer information securely between Building Blocks where communication occurs across the internet.

#### 6.1.2 Adaptor Requirements <a href="#key-requirements" id="key-requirements"></a>

1. Adaptors should _not_ be used for outbound requests.
   1. In general it is the application which manages interactions and requests from various Building Blocks
   2. In the event that a Building Block needs to make a direct request from another Building Block, it is recommended to use the Workflow Building Block to manage and URL and data mapping
2. Adaptors should always be tied to specific products. We will not have universal adaptors. Adaptors will be used to transform data based on specific APIs that have been defined by GovStack.
   1. Adaptor technologies may be re-used for different adaptors or we may have a paradigm where a generic adaptor can be configured via config files
3. Adaptors Perform 3 distinct functions (_all synchronous_):
   1. Class 1 - URL rewriting (mapping a GovStack URL to a URL from a native API)
   2. Class 2 - Payload mapping (transforming data payloads between GovStack and native formats)
   3.  Class 3 - Synchronous 1:many calls and composition of responses into a single response

       _Note: async and/or complex transactions would require the use of the Workflow Building Block_

Please refer to [this document](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/215318576/Adaptor+Concept) for additional context/information and example scenarios for adaptors. \


### 6.2 Native GovStack Implementation

The highest level of integration involves existing products implementing APIs that can be directly consumed by other GovStack Building Blocks. This means that the application will provide APIs that are in alignment with the API specifications for the Building Blocks that they are supporting.

The following diagram shows a complete GovStack deployment with API gateways for citizen access via web or mobile and for existing applications to be able to call GovStack APIs on demand. The workflow building block is used as an adapter, exposing existing applications as GovStack resources via OpenAPI:

![(open in https://app.diagrams.net/)](<../@site/static/img/image6 (2).png>)

Here, citizens and existing applications are provided API access for requests into GovStack via a common API Gateway, while the workflow Building Block adapter provides outgoing API access to existing applications from GovStack Building Blocks.

### 6.3 GovStack Testing Harness

The GovStack team has created a testing platform that allows existing products to validate their APIs against the GovStack specifications. The testing platform consists of a set of tests (written in Gherkin) that can be run against one or more candidate products. These tests are run on a Continuous Integration (CI) platform and are executed automatically whenever changes are made to the GitHub repository for the Building Block.&#x20;

The test platform will provide a detailed output of the test results, showing which tests are passing and failing for each candidate product.&#x20;

The testing platform can be accessed at [https://testing.govstack.global](https://testing.govstack.global)

#### 6.3.1 Adding a new test to the Harness

New tests may be created for a Building Block. These tests are stored in the 'test' directory of the Building Block GitHub repository (GitHub repositories for the various Building Blocks can be found [here](https://github.com/GovStackWorkingGroup)). A new tests can be added by creating a .feature file in the features directory. All tests are written using Gherkin. Note that supporting code to run these tests should be stored in the 'support' folder under features.&#x20;

New tests will automatically be run when a test cycle is started for a Building Block.&#x20;

#### 6.3.2 Adding a new product to the Test Harness

A new candidate product can be integrated into the test harness by adding a new folder to the 'examples' directory of the Building Block GitHub repository (GitHub repositories for the various Building Blocks can be found [here](https://github.com/GovStackWorkingGroup)).&#x20;

The 'examples' folder provides configuration files that will launch the product in the test (CI) environment using docker and docker compose. Testing a new product requires the addition of a new Dockerfile (or set of Dockerfiles) that will build the product, and a docker-compose file and docker-entrypoint.sh file that will launch and configure the product in the test environment so that it is ready to receive the test requests.&#x20;



For more detailed information on how to create new tests or integrate new products into the test harness, please refer to [this document](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/221085697/Steps+to+check+compliance+against+a+GovStack+API+spec), which is geared toward developers and technical teams.&#x20;
