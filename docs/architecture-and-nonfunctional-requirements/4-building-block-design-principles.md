# 4 Building Block Design Principles and Considerations

## 4.1 Design Principles

While the following principles are relevant to many technology deployments, when leveraging the GovStack approach it is important to keep these principles in mind during all phases of design, development, and deployment.

### 4.1.1 Citizen-Centric

Design of systems should be rooted in the needs of the citizens/users of these platforms. A Citizen-centric technology will include the following attributes:

* User-centered design
* Right to be forgotten: everything must be deletable

The best tools evolve from empathizing, understanding and designing for the needs of end-users. Accordingly, we’ve identified a series of use cases and user journeys here: [GovStack Use Cases](https://govstack.gitbook.io/product-use-cases)

Each use case is composed of a collection of modules, or building blocks. As you can see, a relatively small set of these building blocks can be readily applied to a wide variety of applications in low-resource settings.

### 4.1.2 Open <a href="#_hj7wrge29nf5" id="_hj7wrge29nf5"></a>

Where possible, GovStack advocates for the use of open technology, which can reduce cost and help avoid vendor lock-in. Open technology can be defined as:

* Based on open standards
* Based on Digital Development Principles, see [https://digitalprinciples.org/](https://digitalprinciples.org) and [https://digitalinvestmentprinciples.org](https://digitalinvestmentprinciples.org)[/](https://digitalinvestmentprinciples.org)
* Built on open-source software where possible
* Supports open development, see [https://standard.publiccode.net/](https://standard.publiccode.net)
* Cloud native where possible (Docker/Docker Compose/OCI containers)

### 4.1.3 Sustainable <a href="#_5fv1ildee3ef" id="_5fv1ildee3ef"></a>

Any Building Blocks should be developed in a manner which is sustainable and ensures that the technology will continue to be updated and maintained. Some core considerations for sustainability are:

* Stewardship is critical, see [https://publiccode.net/codebase-stewardship/](https://publiccode.net/codebase-stewardship/)
* Continuous funding for maintenance, development and evolution, which results in lower long-term costs
* Uses microservices-based architecture instead of monolithic.
  * This increases interoperability, development and deployment speed and reliability.
  * From Wikipedia: a variant of the[ ](https://en.wikipedia.org/wiki/Service-oriented\_architecture)[service-oriented architecture](https://en.wikipedia.org/wiki/Service-oriented\_architecture) (SOA) structural style – arranges an application as a collection of[ ](https://en.wikipedia.org/wiki/Loose\_coupling)[loosely coupled](https://en.wikipedia.org/wiki/Loose\_coupling) services. In a microservices architecture, services are fine-grained and the protocols are lightweight.

### 4.1.4 Secure <a href="#_1tvbgx5xc0is" id="_1tvbgx5xc0is"></a>

With any technology deployment, security is paramount. Detailed security requirements are defined in the [GovStack Security Requirements](https://govstack.gitbook.io/specification/security-requirements). Beyond those standards, Building Blocks should have the following attributes:

* Building Blocks are audited and certified before being made available
* Development processes and standards enforce quality and security
* Different certification levels reflect level of standards-compliance
* Regular security scanning and auditing
* Public ratings and reviews
* Comprehensive logging and exception handling

### 4.1.5 Accessible <a href="#_64y5ys9r1wf3" id="_64y5ys9r1wf3"></a>

It is vitally important that technology solutions be usable by _all_. Some characteristics of accessible design include:

* Meets users where they are: web, mobile, SMS and/or voice. UI supports accessibility technologies, e.g. screen readers.
* SSO allows for signing in once for multiple services
* Deployment and development processes and standards are open to contributors
* Community-driven development tools for documentation and support
* Blueprints, templates and documentation

### 4.1.6 Flexible <a href="#_ul5nalat80jf" id="_ul5nalat80jf"></a>

GovStack is rooted in the concept that Building Blocks should be re-usable and configurable, such that they can support multiple use cases with minimal effort:

* Building Blocks can be reused in multiple contexts
* Each Building Block is autonomous
* Building Blocks are interoperable, adhering to shared standards
* Building Blocks should be easy to set up
* Standardized configuration and communications protocols should be used to connecting Building Blocks
* Building Blocks can be provided as a service (ICT opportunity)

### 4.1.7 Robust <a href="#_jgyljayvwagf" id="_jgyljayvwagf"></a>

Deployments of Building Blocks should follow these principles:

* Any client-facing functionality should operate in low-resource environments:
  * Occasional power
  * Low bandwidth
  * Low-reliability connectivity
* Easily scalable for high availability and reliability
* API-only based decoupling
* Asynchronous communications pattern decoupled through rooms is ideal
* Eventual consistency for data



## 4.2 Considerations

As with any software implementation, there are constraints and limitations in the GovStack approach that must be addressed. In any country context, there will be deficiencies that present challenges to any technology implementation. In the context of GovStack, the constraints and deficiencies that may be present must be considered at the outset of any project.

&#x20;The following list of potential deficiencies that may be encountered with high-level descriptions should be kept in mind during the development and deployment of any Building Block. Each building block specification SHOULD specify mitigations for these issues:

#### 4.2.1 ICT Governance

Poor or non-existent National ICT governance structure that makes decisions and ensures accountability framework to encourage desirable behavior in the use of ICT in the country. However, this may be described in documents but the implementation is suboptimal or not enforced.

#### 4.2.2 Government ICT policy or Framework

No strategic policy framework for the acquisition and use of IT for social and economic growth in the country. The policy might be at the development stage and where the policy exists, the policy implementation is lagging or non-existent.

#### 4.2.3 ICT infrastructure

The development of IT infrastructure in the country is lagging behind or sub optimal because of poor policies and insufficient investments in the ICT sector. Low coverage of power or the national grid and little penetration of alternative sources of energy especially in the rural.

#### 4.2.4 Financial Resources and Investments in ICT

Limited funding for ICT projects and initiatives. ICT intervention may not be prioritized. No institutionalized or routinized support for ICT projects/ interventions by the government.

#### 4.2.5 ICT Projects/Initiatives

ICT projects and intervention are implemented in a silo, none standard approaches and most of the ICT interventions are proprietary and high cost ventures from private institutions. No national standard architecture for interoperability/ integration of systems

#### 4.2.6 Capacity development and social instruments

Low ICT literacy level among user, None or little research and development done by the national institutions/ academia on the use and scale up ICT in the country. Very few ICT professionals to support large scale ICT projects at national level

#### 4.2.7 Connectivity/Internet access

Lack of or minimum network coverage by GSM and or broadband technologies. Low cellular subscribers per capita and very low internet subscribers per capita. The percentage fibre connectivity in the country is low. A greater percentage of the population do not have computers, laptops or smart phones.

#### 4.2.8 Access to information

Number of household with internet connectivity is concentrated in the urban areas as opposed to rural areas.

#### 4.2.9 Cost competitiveness

Technologies, which are not always ready-for market, are often more expensive than incumbent technologies, without the necessary supportive infrastructure. Competition from existing technologies, including unsustainable technologies

#### 4.2.10 Knowledge and skills

New technologies require specialized knowledge and skills, which are often lacking in host countries where education levels in science, engineering and technology can be low, and emerging areas. ICT specialists is low

#### 4.2.11 Social Legitimacy

New technologies treated with suspicion in local communities especially if prior experience of job losses or unintended social consequences

#### 4.2.12 Cultural barriers

New technologies are seen as a challenge to cultural traditions and communal activities. Technology can also face barriers such as language, role of women in the society, lack of entrepreneurs or dependencies created by decades of development aid



Additionally, the Principles for Digital Development are especially relevant when designing for low resource setting. Refer to [https://digitalprinciples.org/](https://digitalprinciples.org) for information on these Principles.

