![ceramic opengraph](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5e62a54c0e45bd7b2ef53d25_OpenGraphCeramic.png)
 
# **Introduction to the Ceramic Protocol**

This document provides an introduction to the Ceramic protocol. For a technical overview of Ceramic, see technical specification.

- [Introduction](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#introduction)
- [Background](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#background)
- [Document Graph](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#a-scalable-decentralized-document-graph)
- [The Ceramic Ecosystem](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#the-ceramic-ecosystem)
- [Ceramic Ecosystem Alliance (CEA)](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#join-the-ceramic-ecosystem-alliance)
- [Timeline](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#timeline)
- [Additional Resources](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md#additioinal-resources)

---

# Introduction

Ceramic's mission is to create a web without silos.

Ceramic is a permissionless protocol for creating tamper-proof documents. Ceramic documents are signed, append-only objects stored in IPFS, encoded using IPLD, and anchored in one or more blockchains. Ceramic's public document graph provides a single verifiable source of truth for building consensus around important documents, enabling participants to trustlessly share and efficiently coordinate around information in a platform-agnostic way. 

By migrating information from isolated backend servers into the shared public commons governed by digital signatures and consensus, Ceramic solves a range of concerns native to siloed, centralized information including data authorship, ownership, format, availability, access, authenticity, integrity, security, privacy, and state. As a result, the Ceramic network provides the trusted infrastructure needed to enable an internet ecosystem that is boundlessly open, transparent, composable, collaborative, and interoperable.

Ceramic documents are flexible and can be modeled to represent any kind of information, however they seem to be particularly well-suited for storing information which is: 1) relied upon by many different parties; 2) needs elevated trust, auditability, and resilience; 3) requires cross-platform interoperability; and 4) is infrequently updated. In this view, the Ceramic network is ideal for storing platform-agnostic decentralized identifiers and additional data about those identifiers: 

- Decentralized identifiers (DIDs for users, organizations, apps, services, and devices);
- Context for identifiers (descriptors, metadata, routing information);
- Statements about identifiers (verifiable claims, data schema definitions);
- Relationships between identifiers (account links, data mappings, service mappings);
- Policies by identifiers (service policies, privacy policies, access policies, payment policies, permissions); and
- Agreements between identifiers (service agreements).

While Ceramic documents may act as standalone objects, they can also be combined to enable more abstract, novel use cases that demonstrate the potential of user-centric interoperability and the power of the Ceramic network to unbundle user identities, data, and services from applications. By simply combining a few of the documents above, Ceramic can enable: 

- Portable, self-sovereign identity (SSI) systems;
- A global marketplace of interoperable, shared data sources and web services;
- User-managed access control to shared data sourced and services; and
- Pay-as-you-go metered web services.

# **Background**

As developers increasingly build composable applications that rely on user-managed identity, interoperable data, and shared infrastructure, they have less certainty over the types of resources that users will bring to their application at any given time. Because of this, a primary concern for developers is ensuring interoperability between a diverse set of unbundled technologies including (but not limited to) key pairs, wallets, data stores, and infrastructure services. As the variety of infrastructure grows, so does the challenge of maintaining interoperability.

For it to succeed, the composable web needs an identity-centric interoperability protocol to provide applications with the information they need to to easily discover, route to, request access to, and interact with a user's resources regardless of which wallet users bring, which applications created the data, or where the resources are located. 

To provide maximal interoperability, this protocol should allow users to: 1) permissionlessly register an interoperable identity (DID), 2) privately control this identity with one or more private keys, 3) publicly associate public keys and accounts to this identity, 4) associate resources to this identity while maintaining privacy, 5) set permissions for resources, 6) perform access control to resources, and 7) interoperably sign and/or encrypt information. This protocol should also allow: 8) service providers to publish their service definitions and service agreements to the network, and 9) applications to publish their data definitions to the network.

To achieve permissionless interoperability and composabilty across the web, we need a user-centric way to defeat the many identity, data, and service silos that work to undermine these efforts. Ceramic's verifiable document graph offers a solution to these problems.

# A Scalable, Decentralized Document Graph

Ceramic provides a public source of truth for creating and accessing important documents, enabling new use cases that require decentralized coordination or cross-platform interoperability. Because of its hybrid design (IPFS and blockchain), Ceramic's document graph is scalable, decentralized, blockchain-agnostic, efficient, and low cost (variable depending on the blochain anchor service you choose).

### **What is a Document?**

Ceramic documents are signed, append-only, tamper-proof objects stored in IPFS, encoded using IPLD, and anchored in one or more blockchains. Documents are the core construct of the Ceramic protocol and can flexibly be modeled to represent many things. Click here to learn more about how Ceramic documents work.

Ceramic currently supports three standard doctypes, but more can be added to the protocol by submitting an issue on the Ceramic Specs repository.

### **3ID Identity**

3IDs are self-sovereign identities (DIDs) that can authenticate, sign and encrypt data, map to data and services, and perform access control. 3IDs can represent people, organizations, applications, services, or devices and are controlled by one or many private keys, providing flexibility and interoperability across platforms. Learn more about 3IDs here.

### **Account Link**

Account links publicly associate a 3ID to other public identities, such as public keys, smart contracts, or other 3IDs. Account links allow others to verify that two identities are owned by the same person or organization. Learn more about account links here.

### **Policy**

Policies are a flexible way to create single or multi-party statements and can be used to define context for 3IDs (service descriptors, metadata, routing information), statements about 3IDs (application data schema definitions), policies by 3IDs (service policies, privacy policies, access policies, payment policies, permissions), agreements between 3IDs (service agreements), and much more. Learn more about policies here.

### **Additional Doctypes**

Have an idea for a new doctype? Propose it here.

# The Ceramic Ecosystem

Ceramic enables the emergence of a diverse, interoperable ecosystem of user-controlled wallets, data stores, and infrastructure services that allow developers to build lightweight, composable, collaborative applications. Here's how you can get involved.

### Wallets & Authentication Systems

**Integrate Platform-Agnostic, Self-Sovereign Identity**

Give your users a Ceramic 3ID, which is an abstraction from individual key pair and contract accounts that eliminates private key lock-in. DIDs are used for interoperable data signing, encryption, and service authorization with all the wallet keys your users already have.

### Databases

**Unified, User-Mangaged Access Control for Databases**

Make your database's access control system compatible with Ceramic 3IDs so users can manage their information stored across all databases with a single identity and allow different applications to access their information. Ceramic will first support IPFS-based peer-to-peer databases OrbitDB and Textile.

### Infrastructure Services

**Offer Shared, Collaborative Access to Infrastructure Services**

Offer Ceramic-compatible services and list your infrastructure on the Ceramic network to allow various users and applications to gather the information required to interact with your service even if they're not your direct customers. This includes routing information, service agreements, and possibly even payment terms.

### Developers

**Build Composable, User-Centric Applications**

Build your app using Ceramic's ecosystem of connected, interoperable services. Store your user and application data in Ceramic-enabled databases with infrastructure providers that support Ceramic service agreements. Also use Ceramic to discover available data sources to populate your application.

# Join the Ceramic Ecosystem Alliance

The Ceramic Ecosystem Alliance is a collaborative group of organizations, communities, and individuals actively contributing to the research and development of the Ceramic protocol, integrating Ceramic standards into their products, or building services on the Ceramic network. Become a member and [**sign up here**](https://danny765911.typeform.com/to/AAFtVN).

# Timeline

Ceramic's core contributors are working hard to ship v1 of the network. We already have some working code in js-ceramic, and ideally will launch on mainnet sometime this summer. Hop in our Discord to ask more questions.

# Additioinal **Resources**
