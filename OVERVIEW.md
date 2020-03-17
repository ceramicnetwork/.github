![ceramic opengraph](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5e62a54c0e45bd7b2ef53d25_OpenGraphCeramic.png)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![](https://img.shields.io/badge/Chat%20on-Discord-orange.svg?style=flat)](https://discord.gg/6VRZpGP)
[![Twitter](https://img.shields.io/twitter/follow/ceramicnetwork?label=Follow&style=social)](https://twitter.com/ceramicnetwork) 
 
# **Introduction to the Ceramic Protocol**

> Ceramic's mission is to create a web without silos. This document provides an introduction to the Ceramic protocol. For a more technical overview, see [Ceramic Technical Specification](https://github.com/ceramicnetwork/specs).

- [Ceramic Overview](#ceramic-overview)
- [What is stored on Ceramic?](#what-is-stored-on-ceramic)
  - [Decentralized Identifiers (DIDs)](#decentralized-identifiers-dids)
  - [Account Links](#account-links)
  - [Tiles](#tiles)
    - [Schemas](#schemas)
    - [Metadata](#metadata)
    - [Policies](#policies)
    - [Agreements](#agreements)
    - [Claims](#claims)
- [Use Cases](#use-cases)
  - [Self-Sovereign Identity](#portable-self-sovereign-identity)
  - [Interoperable Data](#interoperable-data-ecosystems)
  - [Open Web Services](#open-web-services)
  - [Examples](#examples)
- [Ceramic Ecosystem](#ceramic-ecosystem)
  - [Wallets](#wallets-and-authentication-systems)
  - [Databases](#databases)
  - [Services](#services)
  - [Applications](#applications)
- [Ceramic Ecosystem Alliance](#ceramic-ecosystem-alliance)
- [Timeline](#timeline)


## Ceramic Overview

[**Ceramic**](http://ceramic.network) is a permissionless protocol for creating and accessing mutable, tamper-proof documents that serve as the foundation for a web without silos. Ceramic's public infrastructure provides a censorship resistant, verifiable source of truth for building consensus around important information. By migrating information from isolated servers into the public commons governed by digital signatures and consensus, Ceramic solves a range of concerns native to centralized information silos and paves the way for a more connected, interoperable web.

Although Ceramic can store any type of information, it is ideal for storing information that requires guaranteed trust, cross-platform interoperability, and multi-party consumption. Because participants can create and resolve documents without any centralized service, Ceramic unlocks interoperability between *all platforms and services across the web.* 

For these reasons, Ceramic is especially well-suited as a registry for decentralized identifiers and other documents needed to enable boundless interoperability between a connected ecosystem of users, wallets, applications, databases, and services. This type of a system is critical in today's digital context that seeks to give users more agency and developers more flexibility by unbundling user identities, data, and services from application servers. Some of the things possible with Ceramic include:

- [Portable, self-sovereign identity](#portable-self-sovereign-identity)
- [Interoperable user and application data](#interoperable-data-ecosystems)
- [Open web services](#open-web-services)

> For more information, jump directly to [use cases](#use-cases) or view [examples](#examples).

Ceramic's global ecosystem of interoperable identities, data, and services allows developers to build more composable applications and as a result, Ceramic is the trusted foundation upon which a more connected, transparent, and user-centric internet is built.

### Background

As developers increasingly build composable applications that rely on user-managed identity, interoperable data, and shared infrastructure, they have less certainty over the types of resources that users will bring to their application at any given time. Because of this, a primary concern for developers is ensuring *interoperability* between a diverse set of unbundled technologies including (but not limited to) key pairs, wallets, data stores, and infrastructure services. As the variety of infrastructure grows, so does the challenge of maintaining interoperability.

For it to succeed, the composable web needs a permissionless, identity-centric interoperability protocol to provide applications with all the information they need to easily discover, route to, gain access to, and interact with a user's resources regardless of which wallet users bring, which applications created the data, or where the resources are located. 

To provide maximal interoperability, this protocol should allow participants to: 

1. Permissionlessly register an interoperable identity (DID); 
2. Privately control this identity with one or more private keys;
3. Publicly associate public keys and accounts to this identity;
4. Publicly or privately associate resources to this identity;
5. Set permissions for resources;
6. Perform access control to resources;
7. Interoperably sign and/or encrypt information; and
8. Revoke private keys, public keys, and permissions for resources. 
 
In addition to the requiriements above, this protocol should also allow applications and services to:

9. Publish metadata and definitions;
10. Publish data schemas; and
11. Publish policies and service agreements.

## What is stored on Ceramic?

Ceramic provides a *universal graph of verifiable documents*. Ceramic documents are signed, append-only objects stored in [IPFS](https://github.com/ipfs/ipfs), encoded using [IPLD](https://github.com/ipld/ipld), and anchored in one or more blockchains. Due to its hybrid design relying on IPFS/IPLD and various blockchains, Ceramic's document graph is interoperable, scalable, permissionless, and low cost (variable depending on blochain anchor service). 

Documents are a flexible primitive that can be modeled to represent many things, however each document must conform to a specific *doctype* supported by the protocol. Doctypes specify rules that govern what is a valid update to the document such as signatures and state transitions. This allows Ceramic nodes to verify the state of a given document in a decentralized way.

Ceramic currently supports three standard [doctypes](https://github.com/ceramicnetwork/specs#document-types): [3id](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md), [account-link](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md), and [tile](https://github.com/ceramicnetwork/specs/blob/master/doctypes/tile.md). Below, find some of the common ways that these doctypes are used. If your use case doesn't fit into one of these doctypes, you can add new doctypes to the protocol by submitting an issue on the [Ceramic specs](http://github.com/ceramicnetwork/specs/issues) repository.

>Learn more about [Ceramic documents](https://github.com/ceramicnetwork/specs/blob/master/README.md#protocol-overview).

### Decentralized Identifiers (DIDs)

DIDs are globally unique identities used to sign documents on the Ceramic network and also interact with arbitrary off-chain services and data. More specifically, they are abstract, key-agnostic interfaces used to uniquely identify entities, interoperably sign and encrypt information, authorize authentication/access control to services, and store mappings to additional resources. Ceramic makes no assumptions about what kind of entity a DID represents, so they can be users, organizations, applications, services, devices, etc. Additionally, Ceramic DIDs can be controlled by one or many private keys, providing flexibility and interoperability across wallets and platforms. 

> Learn more about [3IDs](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md) or see an [example](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md#example). Ceramic currently supports the 3ID DID method, but other methods may be added to the network as additional doctypes.

### Account Links

Account links are the second doctype supported by Ceramic. Account links are verifiable public mappings that allow a DID to prove that it owns a different public cryptohraphic identity that is also capable of signing, such as a public key, smart contract, or other DID.

> Learn more about [account links](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md).

### Tiles

Tiles, the third doctype supported by Ceramic, are the most general form of a document and can be used to represent almost any kind of information. Tiles are a way to make verifiable statements by one or more DIDs. Tiles may act as standalone objects or they can reference other tiles. This allows for composability between various tiles, creating a relational graph of verifiable, mutable information.

> Learn more about [tiles](https://github.com/ceramicnetwork/specs/blob/master/doctypes/tile.md).

#### Schemas

The first use case for tiles is creating verifiable, globally-available data schemas. Schema tiles allow a user to define a canonical schema that can be used by anyone anywhere in the world, encouraging multiple parties to converge around standard schemas. This makes schema tiles valuable in their own right. However, schema tiles are also needed to provide structure to information contained in other tiles. Because of this, schema tiles are the core building block for other tiles, such as those below. Schemas tiles can be thought of as templates for other tiles.

#### Metadata

Tiles are used to express additional metadata or context about Ceramic DIDs. At a minimun, DIDs need a DID Manager tile so they can be controlled by one or more private keys. Other metadata needs will vary depending on the type of entity that a DID represents and the use case.

- **DID Manager**: Contains information required to allow one or many private keys to control a DID
- **Public Profile**: Provide context about a DID
  - Basic: General profile metadata such as name, image, logo, etc.
- **Identity Link**: Allow others to verify that a non-cryptographic identifier is owned by a DID
  - Social Links: Public mappings to twitter, github, etc.
  - DNS Links: Public mappings to domain names
- **Resource Link**: Allow others to verify that a resource is owned by the DID
  - Data Links: Mappings to various data sources such as databases, verififiable claims, registries, etc.
  - Service Links: Mappings to services and APIs

#### Policies

Tiles are used to define more explicit, specific terms around the design of a particular service or the access control requirements and permissions needed to access it. For example, policies might define the data model for an application, terms and requirements of a service, or the permissions set by a user to access their data.

- **Collection Policy**: Used to define an app's data model (database types plus references to schema tiles)
- **Service Policy**: ToS and requirements for using a resource, may include service endpoint and payment info
- **Privacy Policy**: User-managed access control permissions to their resources

#### Agreements

Tiles are used to form explicit agreements between DIDs. An example of this would be a **Service Agreement**, which is a multi-party agreement between a provider and purchaser of a service (i.e. data hosting).

#### Claims

Tiles are used to create statements about other DIDs. To achieve this they can create a **Verifiable Claim**, which is a flexible standard for creating signed statements or data. If the verifiable claim is accepted by the recipient, is included in the recipient's metadata above.

## Use Cases

Most production systems and applications will combine multiple DIDs, account links, and tiles to enable extremely powerful use cases that demonstrate the potential of identity-centric interoperability and the unbundling of identities and resources from networks and applications.

### Portable, Self-Sovereign Identity

Self-sovereign identity (SSI) describes a system where participants can permissionlessly create and control their digital identity using one or more private keys. Technically, SSI could be enabled by any decentralized asymmetric cryptography system where public keys (identities) are controlled by private keys (passwords) such as bitcoin or ethereum. However, this type of system is still limited to the network on which these identities are registered, as well as the single private key account. These two constraints function as silos that prevent this identity from being used interoperably in additional contexts.

For identities to be truly flexible and portable across platforms and keys, which makes them more useful in practice, we need an additional identity abstraction that lives at a layer above blockchain accounts. This is the value of DIDs. On Ceramic, DIDs function as the global public identity and they can be controlled by any number of private keys from any blockchain or cryptographic system. DIDs provide a single interface that owners can use to identify themselves, interoperably sign messages, encrypt data, and auhorize/access control to off-chain services that is agnostic to which blockchain a user is on. DIDs are the antidote to private key and network lock-in.

Additionally, SSI is often meant to include much more than direct control of an identifier. Most times, this identifier needs more context so others can interact with it, such as profile details. Ceramic tiles allow DID owners to add metadata and other additional information to their SSI.

DIDs follow a standard specification for base functionality, and there may be many DID providers. Ceramic supports DIDs as doctypes. Currently Ceramic supports the 3ID DID method, but additional methods may be defined in the protocol.

### Interoperable Data Ecosystems

Along with identity portability, it is often desirable to have data portability across applications. This requires a few core functionalities. First, we need to have a universal way to identify a user across platforms, so that we can know which data is theirs. This is handled by SSI/DIDs (see above). Second, we need to know where this data lives. Third, we need to be able to access this data. Last, we need to know the schema of the data so we can consume it in our application without manual processing.

By storing mappings to data resources in a user's DID, Ceramic provides an identity-centric way for data consumers to efficiently discover where information lives, whether on a specific server or a public network. Also by allowing Ceramic DIDs to define access control policies for their data resources, Ceramic provides an identity-centric way for users to provide consumers access to their information regardless of where it lives. Instead of access control happening on the server, it happens directly on the user. And last, Ceramic allows applications to define schemas for their data so that consumers can know a priori the shape of the data that will be returned, even if it is encrypted.

Together these capabilities allow users to frictionolessly control and share their data across various applications.

### Open Web Services

The last piece of the interoperability puzzle is providing more open access to web services. This allows service providers (i.e. data hosting, indexing, anchoring, payments, or other arbitrary web/API services) to service requests from *all* consumers regardless of whether or not they have an account with the service provider. This allows service providers to remove the requirement of consumers creating an account and using an API key to access their service. As a result, services are no longer accessed using an API key from an application's backend, but rather are accessed by meeting certain pre-defined conditions, potentially along with user consent. This allows service providers to grow their customer base on a per-use basis and remove all friction from accessing their services. 

For example, this is required in the case of hosting user data that needs to be accessed by many different parties, most of whom don't have an account with the service. Using Ceramic, the data hosting service can define their service and create a service policy that includes the requirements a consumer must meet in order to access their service. When a user (or application) chooses to use this service to host their data in a database that is access controlled by a Ceramic DID, the user (or app) then adds this resource to their DID. When other consumers want to request this information they need to request access permissions from the user, and once approved, then fulfill the requirments of the hosting service (such as payments or other) before the data will be returned.

Although Ceramic provides the information required for services to accept per-use payments from all parties, the Ceramic protocol itself does not handle payments. Because these transactions will likely be small micropayments, Ceramic is extremely complementary to emerging permissionless cryptographic micropayment networks such as [Connext Network](https://github.com/ConnextProject) on EVM blockchains and [Lightning Network](https://github.com/lightningnetwork/lnd) on Bitcoin. In the most permissionless version of these systems, service providers and end users would run payment nodes and transact. In more practical versions, these responsibilities can be delegated to a third-payment payment processor. This model would also allow applications to pay for services on behalf of their users. We think this make the most sense in the near term.

> Although this example depicts a data hosting service, Ceramic service policies can be used for almost any type of service.

### Examples
To make everything more concrete, let's dive into how [3Box](http://github.com/3box/3box) relies on Ceramic to enable an interoperable, user-controlled data management system. 3Box is a framework that allows developers to store user and application data on a network of open data hosting services access controlled by users instead of on siloed application servers. Users are always in control of their data and can choose to permission it out to other applications, making it shareable across platforms and applications. To achieve this 3Box relies on [self-sovereign identity](#portable-self-sovereign-identity), [interoperable data](#interoperable-data-ecosystems), and [open web services](#open-web-services). 

For self-sovereign identity and to enable user-managed access control, 3Box uses Ceramic's 3ID DID method which allows users to control their identity, information, and services using all of their existing private wallet keys. To enable interoperable data and shared access web services, 3Box relies on the following set of tiles which are created by the various participants including applications, services, and users:

| Tile | Description | Use Case |
| --------------- | ----------- | -------- |
| [Schema(s)]() | Describes a data schema used in a partcicular database | Allows developers to define their data schemas or use existing ones |
| [Collection Policy]() | Describes a collection of databases linked to Schema tiles | Allows applications to define their databases and the data models they use so others can easily consume the data |
| [Service Policy]() | Describes simple functions that take an input and produce an output. In this case, it's used for hosting of databases in the Collection Policy | Allows service providers to define their service or API and the requirements to access it |
| [Privacy Policy]() | Describes user-managed access control rights to databases in the Collection Policy  | Allows users to set permissions and control their privacy while sharing data across apps |

This collection of functionalities allows App A to store data for User B on a hosting service in databases that are access controlled by User B's 3ID. User B can now go to App C and give them permission to access their data from App A. To receive the data from the hosting service, App C must meet the requirements defined by the hosting service's service policy which may include payment information.

## Ceramic Ecosystem

By now you understand that Ceramic enables the emergence of a diverse, interoperable ecosystem of user-controlled wallets, data stores, and infrastructure services that allow developers to build lightweight, composable, collaborative applications. Here's how you can participate.

### Wallets and Authentication Systems

**Integrate Platform-Agnostic, Self-Sovereign Identity**: Give your users a Ceramic 3ID, which is an abstraction from individual key pair and contract accounts that eliminates private key lock-in. DIDs are used for interoperable data signing, encryption, and service authorization with all the wallet keys your users already have.

### Databases

**Integrate a Unified, User-Mangaged Access Control System**: Make your database's access control system compatible with Ceramic 3IDs so users can manage their information stored across all databases with a single identity and allow different applications to access their information. Ceramic will first support IPFS-based peer-to-peer databases [OrbitDB](https://github.com/orbitdb/orbit-db) and [Textile](https://github.com/textileio).

### Services

**Offer Open, Shared Access Services**: Offer Ceramic-compatible services and list your infrastructure on the Ceramic network to allow others to interact with your service even if they're not your direct customers.

### Applications

**Build Composable, User-Centric Applications**: Build your app using Ceramic's ecosystem of connected, interoperable services. Store your user and application data in Ceramic-enabled databases with infrastructure providers that support Ceramic service agreements. Also use Ceramic to discover available data sources to populate your application.

## Ceramic Ecosystem Alliance

The Ceramic Ecosystem Alliance is a collaborative group of organizations, communities, and individuals actively contributing to the research and development of the Ceramic protocol, integrating Ceramic standards into their products, or building services on the Ceramic network. Become a member and [sign up here](https://danny765911.typeform.com/to/AAFtVN).

## Timeline

Ceramic's core contributors are working hard to ship v1 of the network. We already have some working code in [js-ceramic](https://github.com/ceramicnetwork/js-ceramic), and ideally will launch into production sometime this summer. 

Hop in our [**Discord**](https://discord.gg/6VRZpGP) to ask more questions.

## Continue Reading

### [Ceramic Technical Specification  >](https://github.com/ceramicnetwork/specs)
