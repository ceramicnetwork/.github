![ceramic opengraph](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5e62a54c0e45bd7b2ef53d25_OpenGraphCeramic.png)
 
# Introduction to Ceramic
Ceramic's mission is to free the web from gatekeepers and silos.

Ceramic is a permissionless protocol for creating tamper-proof documents. Ceramic documents enable novel use cases such as self-sovereign identity, interoperable data, and user-centric infrastructure that result in more open, composable apps. 

> For a technical overview, see [Ceramic technical specification](http://github.com/ceramicnetwork/specs).

#### Index
- Background
- What is a document?
- Use Cases
- How to Participate
- When is Launch?
- Additional Resources



## Background
Developers are increasingly building composable applications that rely on user-managed identity, interoperable data, and shared infrastructure. In this model, developers have less certainty over the types of resources that users will bring to their application at any given time. Because of this, a primary concern is ensuring interoperability between a diverse set of technologies including (but not limited to) key pairs, wallets, data stores, and infrastructure services. As the variety of infrastructure grows, so does the challenge of maintaining interoperability. 

The composable web is missing a user-centric interoperability protocol to provide applications with the information they need to to easily discover, route to, and interact with a user's resources regardless of which wallet users bring or where their resources are located. To provide maximal interoperability, this protocol should allow users to: 1) permissionlessly register an interoperable identity (DID), 2) privately control this identity with one or more private keys, 3) publicly associate public keys and accounts to this identity, 4) associate resources to this identity without eroding privacy, 5) set permissions for resources, 6) perform access control to resources, and 7) sign and/or encrypt information. This protocol should also allow: 8) service providers to publish their service definitions and service agreements to the network, and 9) applications to publish their data definitions to the network.
 

### A web without silos
To achieve permissionless interoperability and composabilty across the web, we need a way to defeat all silos that work to undermine these efforts by trapping users, information, and other resources. 
- Silos exist in many forms
 - web2 examples: In traditiional cliient-server archcitectures
 - web3 examples
 
Requires coordination between many different parties and services. requires decentralized coordination between a diverse set of participants including end users, wallets, authentication systems, applications, databases, web services, and infrastructure providers. Until now this coordination was highly inefficient at best, and effectively impossible.
 
We need a protocol to create a permissionless source of truth that enables this collaboration.
Efficient coordination requires collective truth. Ceramic is the shared coordination layer where participants can come together to trustlessly manage their identity, easily discover one another, document relationships, and gather the information required to interact. This remains true regardless of which app you're using, wallet you trust, chain you're on, or providers that serve you.
 - controlled by users

needs a user-centric acrhitecture to defeat silos and unbundle appliciations. identity, routing, and access control system. 


## What is a Document?
Ceramic's decentralized network provides permissionless storage for verifiable, updatable documents that can be modeled to represent self-sovereign identities, service agreements, hosting policies, data definitions, access control permissions, payment requirements, and general routing information. These documents collectively liberate our identities and information from the silos that have traditionally kept them locked up.

Ceramic has developed an initial set of standard document types for the use cases above, but this is just the beginning. We expect the community to propose additional document types that extend what's possible on Ceramic.

The Ceramic network is built using existing peer-to-peer technologies including DIDs for identity, IPLD for document formation, and existing blockchains for consensus.

### Supported Doctypes

#### 3ID Identity

#### Account Link

#### Policy

#### Additional Doctypes



## Use Cases

### Self-Sovereign Identity

### Shared Infrastructure

### Interoperable Data

### Verifiable Claims
 

## How can I participate?

**Wallets & Authentication Systems**

Join Ceramic by giving your users a Ceramic DID, which is an abstraction from individual key-pair and contract accounts. DIDs are used for interoperable data signing, encryption, and service authorization with the wallet keys your users already have.

**Databases**

Join Ceramic by making your access control systems compatible with Ceramic DIDs. Ceramic will first support IPFS-based peer-to-peer databases OrbitDB and Textile.

**Infrastructure**

Join Ceramic by publishing your customer service agreements to the network, allowing others to discover where data resides and the payment terms to access it (with user consent).

**Applications**

Join Ceramic by hosting your user and app data in Ceramic-enabled databases with infrastructure providers that support Ceramic service agreements. You can also use Ceramic to discover available data sources to populate your application.

**Developers**

Join Ceramic by building your application or wallet on Ceramic-enabled infrastructure.

**Users**

Ask your wallet provider to support Ceramic DIDs and ask applications to store your data in Ceramic-enabled databases.
 

## When is launch?

The Ceramic core team is working hard to ship v1 of the network, but we could use your help. Join us on Github and Discord to participate.

## More Resources


