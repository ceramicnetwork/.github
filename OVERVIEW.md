![ceramic opengraph](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5e62a54c0e45bd7b2ef53d25_OpenGraphCeramic.png)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![](https://img.shields.io/badge/Chat%20on-Discord-orange.svg?style=flat)](https://discord.gg/6VRZpGP)
[![Twitter](https://img.shields.io/twitter/follow/ceramicnetwork?label=Follow&style=social)](https://twitter.com/ceramicnetwork) 
 
# **Introduction to the Ceramic Protocol**

> Ceramic's mission is to create a web without silos. This document provides an introduction to the Ceramic protocol. For a more technical overview, see [Ceramic Technical Specification](https://github.com/ceramicnetwork/specs).

- [Introduction](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#introduction)
- [Background](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#background)
- [Document Graph](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#a-scalable-decentralized-document-graph)
- [The Ceramic Ecosystem](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#the-ceramic-ecosystem)
- [Ceramic Ecosystem Alliance (CEA)](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#join-the-ceramic-ecosystem-alliance)
- [Timeline](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#timeline)


## Introduction

[**Ceramic**](http://ceramic.network) is a permissionless protocol for creating and accessing tamper-proof, updatable documents that can serve as the foundation for a web without silos. Ceramic's public infrastructure provides a source of truth for important information, removing the problems with isolated servers in favor of a public commons governed by digital signatures and consensus. Ceramic's verifiable and linkable documents removes many obstacles of centralized information silos and enables paves the way for interoperable data, composable web services, and a more connected web.

Ceramic Documents are simple, flexible, network agnostic, and can be modeled to represent any kind of information. They are especially appropriate for representing information which is relied upon by many parties, requires universal resolution and interoperability, and demands guaranteed trust, auditability and resilience. This makes Ceramic well-suited as a permissionless, platform-agnostic registry for decentralized identifiers (DIDs), additional (meta)data about those identifiers, and the policies that define how these identifiers interact with one another. 

Multiple Ceramic documents can be easily combined to enable powerful use cases that are possible when we unbundle data, identities and services from silo'd application servers and instead leverage identity-centric interoperability. To start, Ceramic will power: 

- Portable, self-sovereign identity (SSI) systems;
- User-managed access control to shared data sources and services; 
- Ecosystems of interoperable data sources and composable web services; and
- Permissionless pay-as-you-go web services.

DIDs on Ceramic are abstract, key-agnostic interfaces used to identify unique participants, interoperably sign and encrypt information, authorize authentication to services, store mappings to additional resources, and interact with arbitrary off-chain services and data. Since Ceramic DIDs are documents on the Ceramic network whose signatures (actions) can always be resolved without any centralized service, they unlock interoperability between *all platforms and services across the web.*

Ceramic DIDs can represent any abstract entity (i.e users, organizations, applications, services, devices), and the types of documents can vary widely by use case. For example: 

- Context for DIDs (descriptors, metadata, routing information);
- Statements about DIDs (verifiable claims, data schema definitions);
- Relationships between DIDs (account links, data mappings, service mappings);
- Policies by DIDs (service policies, privacy policies, access policies, payment policies, permissions); and
- Agreements between DIDs (service agreements).

Through the combination of these documents, Ceramic network provides the trusted infrastructure required to enable a more connected, interoperable internet ecosystem that is boundlessly transparent, composable, and collaborative.


## **Properties**

As developers increasingly build composable applications that rely on user-managed identity, interoperable data, and shared infrastructure, they have less certainty over the types of resources that users will bring to their application at any given time. Because of this, a primary concern for developers is ensuring interoperability between a diverse set of unbundled technologies including (but not limited to) key pairs, wallets, data stores, and infrastructure services. As the variety of infrastructure grows, so does the challenge of maintaining interoperability.

For it to succeed, the composable web needs a permissionless, identity-centric interoperability protocol to provide applications with the information they need to to easily discover, route to, request access to, and interact with a user's resources regardless of which wallet users bring, which applications created the data, or where the resources are located. 

To provide maximal interoperability, this protocol should allow users to: 

1. Permissionlessly register an interoperable identity (DID);
2. Privately control this identity with one or more private keys;
3. Publicly associate public keys and accounts to this identity;
4. Publicly or privately associate resources to this identity;
5. Set permissions for resources;
6. Revoke private keys, public keys, and permissions for resources;
7. Perform access control to resources; and
8. Interoperably sign and/or encrypt information. 
 
In addition to the requiriements above, this protocol should also allow applications and services to: 

9. Publish metadata and definitions;
10. Publish data schemas;
11. Publish policies and service agreements.

Ceramic's verifiable document graph offers a solution to these problems.

## A Scalable, Decentralized Document Graph

Ceramic provides a public source of truth for creating and accessing important documents, enabling new use cases that require decentralized trust, coordination, or cross-platform interoperability. Because of its hybrid design (IPFS and blockchain), Ceramic's document graph is scalable, decentralized, blockchain-agnostic, efficient, and low cost (variable depending on the blochain anchor service you choose).

### **What is a Document?**

Ceramic documents are signed, append-only objects stored in [IPFS](https://github.com/ipfs/ipfs), encoded using [IPLD](https://github.com/ipld/ipld), and anchored in one or more blockchains.  Documents are the core construct of the Ceramic protocol and can flexibly be modeled to represent many things. Ceramic currently supports three standard [doctypes](https://github.com/ceramicnetwork/specs#document-types), but more can be added to the protocol by submitting an issue on the [Ceramic Specs](http://github.com/ceramicnetwork/specs/issues) repository.

>Learn more about how [Ceramic documents work](https://github.com/ceramicnetwork/specs/blob/master/README.md#protocol-overview).

### **3ID Identity**
3ID is a decentralized identity (DID) method that uses Ceramic to create, update, and resolve DID documents. The DID standard provides a general format for verifiable decentralized digital identities. Given a specific DID string, a DID document which contains public keys, services, authentication authorization, etc. can be resolved.

Ceramic's 3IDs allow users to authenticate, sign and encrypt data, map to data and services, and perform access control. 3IDs can represent people, organizations, applications, services, or devices and are controlled by one or many private keys, providing flexibility and interoperability across platforms. 

> Learn more about 3IDs [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md) and see an example [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md#example).

### **Account Link**
Account links publicly associate a 3ID to other public identities, such as public keys, smart contracts, or other 3IDs. Account links allow others to verify that two identities are owned by the same person or organization. 

> Learn more about account links [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md) and see examples [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md#examples).

### **Policy**
Policies are a flexible way to create single or multi-party statements and can be used to define context for 3IDs (service descriptors, metadata, routing information), statements about 3IDs (application data schema definitions), policies by 3IDs (service policies, privacy policies, access policies, payment policies, permissions), agreements between 3IDs (service agreements), and much more. 

The policy doctype can be used to descibe services that are made available though through the Ceramic network. A service provider creates a policy document that includes the description of the api that can be used to reach the service (e.g. http api, libp2p protocol, etc). The policy document may also include payment information, i.e. if some form of payment is needed in order to use the service.

Using Ceramic Service policies almost any type of services can be represented. Some examples of this include Payments, Data hosting, Indexing, etc. Adding a service to ceramic allows it to be used in a user centric way. Services can be enabled per user and apps can route to different services though the users identity.

> Learn more about policies [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/policy.md) or see examples [here](https://github.com/ceramicnetwork/specs/blob/master/doctypes/policy.md#examples).

#### Policy Templates
Here are some example templates to give you an idea of what's possible with policies, but you can always create your own based on your use case.

| Policy Template | Description | Use Case |
| --------------- | ----------- | -------- |
| [Collection Policy]() | Describes a collection of databases with specific schemas | Useful for apps to define their data model, so others can easily consume the data |
| [Service Policy]() | Describes simple functions that take an input and produce an output, but could also be used for more complex services such as database hosting, etc. | Useful for infrastructure service providers to define their service or API | Useful for  |
| [Privacy Policy]() | Describes access control rights to databases in a Collection Policy  | Useful for allowing users to set permissions and control their privacy while sharing data across apps |

> [3Box](http://github.com/3box/3box) uses these templates to enable an interoperable, user-controlled data management system.


### **Additional Doctypes**

> Have an idea for a new doctype? Propose it [here](http://github.com/ceramicnetwork/specs/issues).

## The Ceramic Ecosystem

Ceramic enables the emergence of a diverse, interoperable ecosystem of user-controlled wallets, data stores, and infrastructure services that allow developers to build lightweight, composable, collaborative applications. Here's how you can get involved.

### Wallets & Authentication Systems

**Integrate Platform-Agnostic, Self-Sovereign Identity**: Give your users a Ceramic 3ID, which is an abstraction from individual key pair and contract accounts that eliminates private key lock-in. DIDs are used for interoperable data signing, encryption, and service authorization with all the wallet keys your users already have.

### Databases

**Integrate a Unified, User-Mangaged Access Control System**: Make your database's access control system compatible with Ceramic 3IDs so users can manage their information stored across all databases with a single identity and allow different applications to access their information. Ceramic will first support IPFS-based peer-to-peer databases OrbitDB and Textile.

### Infrastructure Services

**Offer Shared, Collaborative Access Services**: Offer Ceramic-compatible services and list your infrastructure on the Ceramic network to allow various users and applications to gather the information required to interact with your service even if they're not your direct customers. This includes routing information, service agreements, and possibly even payment terms.

### Developers

**Build Composable, User-Centric Applications**: Build your app using Ceramic's ecosystem of connected, interoperable services. Store your user and application data in Ceramic-enabled databases with infrastructure providers that support Ceramic service agreements. Also use Ceramic to discover available data sources to populate your application.

## Join the Ceramic Ecosystem Alliance

The Ceramic Ecosystem Alliance is a collaborative group of organizations, communities, and individuals actively contributing to the research and development of the Ceramic protocol, integrating Ceramic standards into their products, or building services on the Ceramic network. Become a member and [sign up here](https://danny765911.typeform.com/to/AAFtVN).

## Timeline

Ceramic's core contributors are working hard to ship v1 of the network. We already have some working code in [js-ceramic](https://github.com/ceramicnetwork/js-ceramic), and ideally will launch into production sometime this summer. 

Hop in our [**Discord**](https://discord.gg/6VRZpGP) to ask more questions.

## Continue Reading

### [Ceramic Technical Specification  >](https://github.com/ceramicnetwork/specs)
