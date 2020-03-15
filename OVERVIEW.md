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

[**Ceramic**](http://ceramic.network) is a permissionless protocol for creating and accessing mutable, tamper-proof documents. Ceramic's public infrastructure provides a censorship resistant, verifiable source of truth for building consensus around important information. By migrating information from isolated servers into the public commons governed by digital signatures and consensus, Ceramic solves a range of concerns native to centralized information silos. 

Although Ceramic can store any type of information, it is ideal for storing information that requires guaranteed trust (availability, auditability), cross-platform interoperability (universal resolvability), and multi-party consumption. Because participants can create and resolve documents without any centralized service, Ceramic unlocks interoperability between *all platforms and services across the web.* 

For these reasons, Ceramic is especially well-suited as a permissionless, platform-agnostic registry for decentralized identifiers, additional metadata about those identifiers, and the policies that define how these identifiers interact with one another. Together, these primitives unlock a set of new use cases that are critical in today's digital context that seeks to give users more agency and developers more flexibility by unbundling user identities, data, and services from application servers:

- Portable, self-sovereign identity
- Interoperable user and application data
- Open, pay-per-use web services
- User-managed access control to data and services

This provides users, applications, and services with a shared, interoperable environment to identify and interact online. As a result, Ceramic provides the trusted public infrastructure required to enable a more connected, interoperable internet ecosystem that is boundlessly transparent, composable, and collaborative.

> For a real world example, see the [Use Cases & Applications] section below.

### Background

As developers increasingly build composable applications that rely on user-managed identity, interoperable data, and shared infrastructure, they have less certainty over the types of resources that users will bring to their application at any given time. Because of this, a primary concern for developers is ensuring *interoperability* between a diverse set of unbundled technologies including (but not limited to) key pairs, wallets, data stores, and infrastructure services. As the variety of infrastructure grows, so does the challenge of maintaining interoperability.

For it to succeed, the composable web needs a permissionless, identity-centric interoperability protocol to provide applications with all the information they need to easily discover, route to, gain access to, and interact with a user's resources regardless of which wallet users bring, which applications created the data, or where the resources are located. 

### Requirements

To provide maximal interoperability, this protocol should allow users to: 1) permissionlessly register an interoperable identity (DID); 2) privately control this identity with one or more private keys; 3) publicly associate public keys and accounts to this identity; 4) publicly or privately associate resources to this identity; 5) set permissions for resources; 6) perform access control to resources; 7) interoperably sign and/or encrypt information; and 8) revoke private keys, public keys, and permissions for resources. 
 
In addition to the requiriements above, this protocol should also allow applications and services to: 9) publish metadata and definitions; 10) publish data schemas; and 11) publish policies and service agreements.

## Ceramic: A Universal Document Graph

Ceramic documents are signed, append-only objects stored in [IPFS](https://github.com/ipfs/ipfs), encoded using [IPLD](https://github.com/ipld/ipld), and anchored in one or more blockchains. Documents are the core construct of the Ceramic protocol and can flexibly be modeled to represent many things. 

Documents can be used to descibe identities, applications, or services that are made available though through the Ceramic network. For example a service provider can create an identity and a policy document that includes the description of the api that can be used to reach the service (e.g. http api, libp2p protocol, etc). The policy document may also include payment information, i.e. if some form of payment is needed in order to use the service.

Ceramic currently supports three standard [doctypes](https://github.com/ceramicnetwork/specs#document-types) ([3id](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md), [account-link](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md), [policy](https://github.com/ceramicnetwork/specs/blob/master/doctypes/policy.md)), but more can be added to the protocol by submitting an issue on the [Ceramic Specs](http://github.com/ceramicnetwork/specs/issues) repository.

Due to it's hybrid design relying on IPFS/IPLD and various blockchains, Ceramic's document graph is interoperable, scalable, permissionless, and low cost (variable depending on blochain anchor service).

>Learn more about how [Ceramic documents work](https://github.com/ceramicnetwork/specs/blob/master/README.md#protocol-overview).

### Decentralized Identifiers (DIDs)

Ceramic DIDs are globally unique identities used to sign documents on the Ceramic network and also interact with other arbitrary off-chain services and data. DIDs are abstract, key-agnostic interfaces used to identify participants, interoperably sign and encrypt information, authorize authentication/access control to services, and store mappings to additional resources. Ceramic makes no assumptions about what kind of entity a DID represents, so they can be users, organizations, applications, services, devices, etc. Additionally, Ceramic DIDs can be controlled by one or many private keys, providing flexibility and interoperability across wallets and platforms. 

> Ceramic currently supports the 3ID DID method. [Learn more about 3IDs](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md) or see an [example](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md#example).

### Metadata

Ceramic DIDs will likely want to express additional metadata or context about themselves. Depending on the type of entity that a DID represents this may vary. A few examples:

- Public Profiles: Provide context about a DID
  - Basic: General profile metadata such as name, image, logo, ...
  - Descriptors: More complete descriptions for services, apps, ...
- Identity Links: Allow others to verify that two identities are owned by the same DID
  - Account Links: Public mappings to public keys, smart contracts, other DIDs, ...
  - Social Links: Public mappings to twitter, github, ...
  - DNS Links: Public mappings to domain names
- Resource Links: Allow others to verify that a resource is owned by the DID
  - Data Links: Mappings to various data sources such as databases, verififiable claims, registries, ...
  - Service Links: Mappings to services and APIs

### Policies

Ceramic DIDs will also likely want to define explicit policies that govern various things about their identity or resources that help others others interact with them. A few examples:

- Schema Policies: Define schemas for data
- Collection Policies: Define an app's data model (database types plus schema policies)
- Service Policies: ToS for using a resource, may include service endpoint and payment info (i.e. anchoring, data hosting, indexing
- Privacy Policies: User-defined access control permissions for their resources

### Agreements

Ceramic DIDs may want to form explicit agreements between one another. An example of this would be a service agreement, which is a multi-party agreement between a provider and purchaser of a service (i.e. data hosting).

### Claims

Ceramic DIDs may want to create statements about other DIDs. To achieve this they can create a verifiable claim, which is a flexible standard for creating signed statements or data. If the verifiable claim is accepted by the recipient, is included in the recipient's metadata above.

## Use Cases & Applications

Although Ceramic documents can act as standalone objects, most production systems and applications will combine multiple documents to enable extremely powerful use cases that demonstrate the potential of identity-centric interoperability and the unbondling of identities and resources from applications.

### Portable, Self-Sovereign Identity (SSI) Systems


### Interoperable Data Ecosystems

### Open Web Services
Using Ceramic service policies almost any type of services can be represented. Some examples of this include Payments, Data hosting, Indexing, etc. Adding a service to ceramic allows it to be used in a user centric way. Services can be enabled per user and apps can route to different services though the users identity.

### Example: 3Box
[3Box](http://github.com/3box/3box) uses these three use cases to enable an interoperable, user-controlled data management system.

| Policy Template | Description | Use Case |
| --------------- | ----------- | -------- |
| [Collection Policy]() | Describes a collection of databases with specific schemas | Useful for apps to define their data model, so others can easily consume the data |
| [Service Policy]() | Describes simple functions that take an input and produce an output, but could also be used for more complex services such as database hosting, etc. | Useful for infrastructure service providers to define their service or API | Useful for  |
| [Privacy Policy]() | Describes access control rights to databases in a Collection Policy  | Useful for allowing users to set permissions and control their privacy while sharing data across apps |

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
