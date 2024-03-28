# 3 GovStack Architecture

The following diagram provides an example of a GovStack implementation

<figure><img src="../@site/static/img/GovStack Overall Architecture.png" alt=""><figcaption></figcaption></figure>

This digram shows an example of what a GovStack implementation may look like in practice. Several concepts that are important to GovStack are shown in this diagram:

* A GovStack implementation may consist of multiple ‘applications’, each serving a distinct purpose. The value that GovStack provides is that these applications do not have to be developed from scratch, but rather leverage core functionalities that are provided by various Building Blocks. And these Building Blocks may be used in multiple applications.
* Applications may access outside services through the Information Mediator. Access to these services are configured within the Information Mediator per organization. One application may have permission to access data provided by a particular ministry that another application may not access.
* A GovStack application can be used by different types of users. The roles and permissions for various user groups must be managed by the application itself (using [authorization services described here](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/239370263))
* Building Blocks may be based on existing applications or Digital Public Goods (DPGs). These DPGs may have an API that conforms with the GovStack API specification for that Building Block. If not, an [adaptor](https://govstack-global.atlassian.net/wiki/spaces/GH/pages/215318576) can be used to map the existing API to the GovStack API
* The Application frontend and backend may use any mechanism to communicate (REST, GraphQL, etc). However, all GovStack API calls should be done using standard REST protocols.



## 3.1 GovStack Components

In a GovStack implementation, there are several different types of components. In addition, there are components that must be developed to support the testing and compliance process for a particular building block. This document provides a definition of these various components as well as detailing which components are generic (may be used for multiple use cases) and which are specific to a particular use case. This document will also flag any components that are specific to the GovStack sandbox/demonstration platform.

### 3.1.1 Use Case Dependent <a href="#use-case-dependent" id="use-case-dependent"></a>

* **Application Frontend.** For a particular use case, a user interface will be implemented to provide necessary information to the user and collect any needed information from the user.
* **Application Backend**. For a use case, the application backend will manage the flow and business logic needed. The backend will access any local data and make calls to GovStack Building Blocks as needed.
* **Repositories**. An application may have a local repository that contains data that is specific for that use case.
* **BB Emulator**. This component is applicable only to the GovStack sandbox/demonstration platform. In some cases, a simple/lightweight implementation of a Building Block has been created to provide the needed BB functionality for a particular use case. This reduces the infrastructure load for the sandbox.

### 3.1.2 Generic  <a href="#generic" id="generic"></a>

These components may be adapted to a country specific context, but can be generic across multiple use cases in a particular GovStack implementation.

* **BB candidate software.** This is a specific software platform that functions as one or more building blocks in a GovStack implementation.
* **Adapter.** The adaptor provides a mapping from an existing software platform’s API to the format that is specified by the GovStack BB spec for a particular Building Block
* **BB Configuration files.** These are the Docker files and startup scripts that allow a product to be automatically launched and configured in a GovStack environment.
* **Test Harness Scripts.** These scripts configure any data or environment that is needed for a candidate application to be able to pass the tests for a particular Building Block in the testing application
* **Repositories**. As noted, some repositories may contain use-case specific data. However, there may also be repositories that are needed by multiple applications or use cases.

