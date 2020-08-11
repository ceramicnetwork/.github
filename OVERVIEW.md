![](https://uploads-ssl.webflow.com/5ebcbef3ac4954196dcdc7b5/5f30d276e0a2e410f229f1a6_ceramicgithubwhite.png)
# Ceramic: A Dynamic, Peer-to-Peer Data Management System
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![](https://img.shields.io/badge/Chat%20on-Discord-orange.svg?style=flat)](https://discord.gg/6VRZpGP)
[![Twitter](https://img.shields.io/twitter/follow/ceramicnetwork?label=Follow&style=social)](https://twitter.com/ceramicnetwork) 


> Ceramic is a dynamic information management protocol for the open web.


## Abstract
This paper describes [**Ceramic**](http://ceramic.network), a peer-to-peer platform for building decentralized applications using smart documents. The Ceramic protocol allows anyone to permissionlessly store and manage dynamic content on the internet in a secure, collaborative, and trust-minimized manner. The Ceramic platform allows anyone to securely manage mutable content in a trust-minimized and peer-to-peer way. Ceramic's decentralized content management framework eliminates the need for relying on servers in order to guarantee the state or integrity of information. Ceramic achieves this by combining a peer-to-peer network, cryptographic append-only logs, programmable document logic, and blockchain anchoring to guarantee strict state management and version control of documents that may change or need to be edited over time. 

The *Ceramic Network* is a . *Smart Documents* is a specification for creating and interacting with smart documents. Smart documents provide developers with a decentralized way of managing individual units of dynamic content in a way that hasn't been possble before. Smart documents allow content to be programmed, strictly ordered, etc. In a way, smart documents allow for programmable content in the same way that smart contracts allowed for programmable for money. *Ceramic Nodes* perform the heavy-lifting within the network. The *Ceramic Network* is a decentralized, peer-to-peer network for storing and managing smart documents. Ceramic's public, permissionless infrastructure provides a verifiable, censorship-resistant source of truth for important information. All documents managed on the network are publicly discoverable and openly available for anyone else to consume, encouraging collaboration and unlocking composabilty of content. 

Together, smart documents and the Ceramic network provide a complete decentralized content management platform that can be used to implement use cases such as [decentralized identity management](#identity-management), [shared schemas](#schemas), [social media content](#social-media-content), [data storage](#data-storage), [websites & CMS](#websites-cms), and more. Jump to [use cases](#use-cases).

For a more technical overview, see [Ceramic Technical Specification](https://github.com/ceramicnetwork/specs).


## 1. Introduction
The Web3, or Dweb, movement aims to allow developers to build next-generation applications using peer-to-peer content protocols and services. Developers may choose to add Web3 infrastructure to their application for a variety of reasons including byt not limited to distributing responsibility, opening access, improving collaboration, lowering costs, guaranteeing trust/security, or giving users control of their information. The potential benefits of rearchitecting the way content is managed online are trenendous, however unlike the rapid innovation we've witnessed in decentralized finance (i.e. DeFi), we have not seen the same level of development, innovation, or maturity in decentralized data. As a result, the adoption of Web3 has lagged other applications of decentralized technology.


### 1.1 Data Management Systems: Cloud Hosted or Decentralized and Static
One of the primary reasons why Web3 has not progressed as fast as its decentralized counterparts is because the Web3 development "stack" is incomplete. Currently developers wanting to manage data for their application are limited to a few choices: centrally-hosted traditional databases ([SQL]()), centrally-hosted p2p databases ([Textile Threads](), [OrbitDB]()), decentralized file storage networks ([Filecoin](), [Arweave](), [Sia]()), blockchains ([Ethereum](), [Flow](), [Near]()), or local storage (in-browser). Although each option may have merit for specific use cases, there exists an obvious capability gap somewhere between dynamic centralized databases and static decentralized files. There is no way to manage dynamic, mutable content in a purely decentralized and peer-to-peer manner. 
Related Work, File Storage Networks, Blockchains, P2P DBs

One of the primary reasons why Web3 has not progressed as fast as its decentralized counterparts is because the Web3 development "stack" is incomplete. Currently developers wanting to manage data for their application are limited to a few choices: centrally-hosted traditional databases ([SQL]()), centrally-hosted p2p databases ([Textile Threads](), [OrbitDB]()), decentralized file storage networks ([Filecoin](), [Arweave](), [Sia]()), blockchains ([Ethereum](), [Flow](), [Near]()), or local storage (in-browser). Although each option may have merit for specific use cases, there exists an obvious capability gap somewhere between dynamic centralized databases and static decentralized files. There is no way to manage dynamic, mutable content in a purely decentralized and peer-to-peer manner. 
Related Work, File Storage Networks, Blockchains, P2P DBs

### 1.2 Ceramic: Peer-to-Peer Programmable Data
Ceramic aims to fill this gap with *smart documents*. Smart documents turn static files into dynamic objects with permalinks, versions, capabilities, and logic not possible on a centralized database or a decentralized file store/blockchain. Smart documents manage content according to a set of programmable rules. Simple programs may enforce that only owners can update content, but more complex programs may mutate content based on external actions such as the change in a related document. From state transition rules to complex operations, smart documents allow you to program content in the same way that smart contracts have allowed you to program money.
Dynamic data.

Ceramic aims to fill this gap with *smart documents*. Smart documents turn static files into dynamic objects with permalinks, versions, capabilities, and logic not possible on a centralized database or a decentralized file store/blockchain. Smart documents manage content according to a set of programmable rules. Simple programs may enforce that only owners can update content, but more complex programs may mutate content based on external actions such as the change in a related document. From state transition rules to complex operations, smart documents allow you to program content in the same way that smart contracts have allowed you to program money.
Dynamic data.


### 1.3 Design Goals
The Ceramic Network is a trusted, peer-to-peer, dynamic information management platform for building next-generation decentralied applications. The Ceramic network has been designed from the ground up to handle extreme scale, be customizable, ensure trust,


#### 1.3.1 Secure, Scalable Version Control
One of the primary decisions to make when designing a peer-to-peer data management system is how to properly handle *version control and state management* of documents which may change or evolve over time. Such a system is important as it serves as the primary mechanism for handling conflicting updates without the use of a trusted server. We evaluated many different existing approaches to this problem, each possessing their own strengths, weaknesses, and use cases. For example, many blockchains such as [Ethereum]() employ a [consensus algotithm](https://en.wikipedia.org/wiki/Consensus_algorithm) which gurantees strict ordering of all transactions on the network over a global state, which provides strong security and finality guarantees but suffers from scalability issues. On the other hand, many peer-to-peer databases such as [OrbitDB]() and content collaboration platforms such as [Matrix]() utilize a [conflict-free replicated data type](https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type) (CRDT) data structure which provides good scalability by using local-first, eventually-consistent state management for each document but occassionally suffers from inconsistencies and provides no global state of all documents, since each document state is handled individually. As you can imagine, the difference is what makes blockchains great at managing financial assets and CRDT systems great at fostering realtime, multi-party collaboration.

When considering the design of the state management system for Ceramic, we wanted the best of both approaches: *security and scalability*. Ceramic documents should be able to securely manage data related to sensitive cryptographic operations such as decentralized identities, document ownership changes, and key rotations. These operations cannot tolerate eventual consistency and therefore require the strict ordering and finality provided by blockchain consensus. However, the Ceramic network will collectively need to manage an extreme number of documents simultaneously and would quickly outgrow the scaling limitations experienced by blockchains with one ever-growing global state. For these reasons, Ceramic implements a document-centric state management protocol which provides strict ordering over updates within each document without requiring the network to maintain any global state. We achieve this with *DocState*. DocState consists of timestamping (anchoring) a document's updates into a blockchain, causing each document to form it's own immutable "doc-chain." By foregoing global state in favor of DocState, Ceramic can horizontally scale to handle an extremely large amount of information without creating one ever-growing ledger, while also allowing nodes to be run in resource-contstrained environments such as browsers and mobile/IoT devices.


#### 1.3.2 Programmable State Transition Logic
Another important consideration in any peer-to-peer system that seeks to manage dynamic, mutable information is how to handle document *state transitions* in a decentralzed but flexible way. State transition logic defines what constitutes a valid update to a document. For example, if an update is made to a given document that adheres to its defined state transition logic, then the update would be considered valid by the protocol and a new version would be created using the DocState system described above. Many peer-to-peer data management systems have a simply defined state transition ruleset that is generally applied to every document: if you are the owner of the document, you are allowed to make updates to it. However, there are lessons to be learned from smart contract blockchains such as Ethereum, which allow developers to program state transition logic for assets in a flexible way. For example, on Ethereum you could write a simple contract that says *do X if Y occurs*. State transition programmability is a powerful primitive that we have not yet seen applied to decentralized data, likely because most data systems are CRDT-based and don't utilize strict ordering.

When designing the document state transition system for Ceramic, we wanted to ensure that documents could be programmed in the same way as smart contracts. This is the reason Ceramic documents are called *smart documents*. Ceramic allows developers to write programs that govern the state transition rules of a document with explicit logic and rules, which could fall anywhere on the spectrum from simple (i.e. "update the document if signed by the owner(s)") to moderate (i.e. "update the document if signed by the owner(s) and the update adheres to the document's defined content format and schema") to complex (i.e. "update the document to Y if X external event happens such as the change in a related document"). Ceramic achieves this with *doctypes*. Doctypes are software packages that contain the state transition logic which is to be applied to a document. On Ceramic, every document must specify a doctype and these rules will be enforced nodes running the protocol.


#### 1.3.3 Universal Data Discovery, Collaboration, and Composability
Most information on the internet today is trapped on proprietary cloud server silos where it is safeguarded by a single gatekeeper and only provides utility for the application or service provider hosting the data. At the time when cloud was invented, it was a dramatic improvement over on-prem or local data storage solutions because it provided availability, performance, and removed the need for users to self-host, but had the tradeoff of providing users with less control. In order to access or update this information, a user or third-party would need to somehow discover the server, authenticate using an appliciation-specific login, examine the data that was available, and gather the schema (which is often proprietary) so the data could be interpreted. This application-centric (or server-centric) framework for managing data results in needless risk on data custodians, duplication of information and infrastructure, and restriction of open access. As a result, centralized information servers limit the cooperative and cross-platforms sharing of data. For many reasons beyond the scope of this paper, many developers are instead opting to build on new architectures without these limitations and costs.

A primary aim of the decentralization movement is to liberate information from centrally-hosted servers and migrate it to a public, permissionless context where it can be universally accessed, easily shared, and built upon by others in new ways. This is often referred to as *composability*. You can witness the transformative power of open, composable data today in realtime with the proliferation of the decentralized finance (DeFi) ecosystem on Ethereum. Since Ethereum is a public and permissionless network, every smart contract deployed on the network can be discovered and utilized by any other application or protocol. By lowering the barrier to development and participation, this open finance ecosystem has unlocked a massive wave of creativity and innovation. In the process, it has also generated a tremendous amount of collective societal value. Anecdotally, this is why people often refer to Ethereum smart contract primitives and protocols as "money legos."

In the same way that Ethereum has provided a universal platform for money legos, Ceramic aims to provide a universal platform for data legos. By offering a public and permissionless data management context that makes data openly available, Ceramic allows anyone create, discover, and share documents across applications or platforms without the aforementioned limitations of siloed servers. Because participants can create and resolve documents for any type of information without any centralized service, Ceramic unlocks information interoperability between *all platforms and services across the web*. This makes Ceramic ideal for storing information that requires guaranteed trust, cross-platform interoperability, and multi-party consumption. With Ceramic, anyone can openly save, query, and interact with documents stored on the network as opposed to needing to gain access to a given server. Furthermore, existing documents can be referenced, linked, or built upon and extended by other documents in various ways. In addition to providing composability between documents on-network, Ceramic also provides composability to resources stored off-network. By storing a reference to a database server, a decentralized file, or a smart contract registry hosted off-network (and the schema of the data stored there), Ceramic documents can also function as hyperlinks which provide interoperability and composability to ny off-network resource. This type of a hybrid document management system enables content collaboration on a scale that was previously unimaginable. Ceramic's global ecosystem of discoverable and interoperable data resources can serve as the foundation for a web without silos, allowing developers to build composable applications with unprecedented modularity, trust, and scale, regardless of whether the content is actually stored on Ceramic or not.


#### 1.3.4 Configurable, Complimentary Infrastructure
When it comes to data management, developers may choose to build with a variety of different technologies that are best suited to their specific use case. As a peer-to-peer data management platform that intends to unify the web's information into a single open context, Ceramic doesn't seek to replace any of the infrastructure that you may already be building with or comfortable using. In fact, Ceramic was designed to be completely configurable so that it can be used to *compliment*, rather than replace, the rest of your technology stack. Ceramic delivers on this in a handful of ways. Smart documents can backup and persist their content to whichever storage infrastructure you prefer, including decentralied networks ([IPFS](), [Filecoin](), [Sia](), [Arweave]()) or centralized database servers ([SQL](), [Redis](), [MongoDB]()). Smart documents can anchor updates on whichever blockchain or consensus system you prefer ([Ethereum](), [Flow](), [Cosmos](), [Near]()). Smart documents can invoke scripts on whichever compute platform you prefer (blockchains, servers). And smart documents can be used to augment and extend your existing data management systems such as traditional databases, p2p databases ([Textile](), [OrbitDB]()), decentralized file storage platforms, and more with public discoverability, routing, user-managed access control, and schemas as described in the section above.


#### 1.3.5 DID-Based Identity Providers
Ceramic foregoes the lock-in of a proprietary user account or identity system in favor of interoperability and simple integration with other identity providers and technologies. Ceramic's only identity requirement is that users interact with smart documents on the network using a W3C-compliant [decentralized identifier](https://www.w3.org/TR/did-core/) (DID) that adheres to the DID Provider standard. Any DID from any provider can be supported by the network, and currently there are more than 40 DID providers with working implementations including Ceramic 3ID, Microsoft Ion, Ethereum ethr-did, and so on. This DID-based, but provider-agnostic design makes Ceramic's user model extremely flexible and interoperable with other technologies. Various DID methods such as the [3ID (CIP-6)]() DID method native to Ceramic can be connected to and controlled by one or many different wallet account key pairs from any blockchain network or crytographic technology, so users can interact with Ceramic using the key pairs or wallets that they may already be using for your application.


## 2. System Features

### 2.1 Smart Documents
Smart documents are the core unit of information on the Ceramic network. A smart document is an append-only log of sequential records that are anchored in a blockchain. Every smart document adheres to the same general structure, which is outlined below. They are mutable, tamper-proof files whose content rules and update logic can be programmed with guaranteed execution. Smart documents transform content from static files into dynamic objects. Smart documents can exist as independent objects or can be linked together to form a graph of related information. and associated metadata that governs how the protocol handles the documents. State management for content. Doc-chains. Programmabilty, state transititions, rules, and logic that will be enforced by the protocol. Strict ordering.

</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
• INSERT VISUAL OF A DOCUMENT •
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>

#### 2.1.1 DocIds
Immutable permalinks. A unique, immutable document identifier similar to a permalink. DocIds never change, even if the document is updated thousands of times. DocIds are the canonical reference to a document and are used to query the current version of the document from nodes. The DocID contains important information including the networkID of the Ceramic network on which this document belongs.

#### 2.1.2 Document Log
Append-only log of records. Documents are modeled as an append-only log of linked records that makes up a document. The document log can be thought of as a "doc-chain."

#### 2.1.3 Records
Individual records (genesis, signed, anchor) that make up the document log. Smart documents can store a variety of data, ranging from JSON content to execution scripts. What each document can store is defined by a combination of its doctype and schema.

#### 2.1.4 Timestamps
Blockchain anchoring and ordering. Documents need to specify a blockchain for anchoring document updates. Blockchains provide strict ordering to records and trust to document state. Versions: New document versions are created every time an anchor record (signifying a blockchain transaction) is added to the document log. Historical versions of a document can be referenced or queried by appending the versionID to the docID.

#### 2.1.5 Doctypes
Logic engines. The document's smart engine. Doctypes describe the content rules and state transition logic that governs the document. Rules specified by doctypes are enforced by the protocol every time an update is made to a document. A number of community-developed doctypes can be found in Ceramic [CIPs](), and three doctypes are included by default in every node: [Tile (CIP-N)](), [3ID (CIP-N)](), and [Account Link (CIP-N)]().

#### 2.1.6 Hooks
Document micro-programs

#### 2.1.7 Metadata
Owners, Schemas, and Tags: A schema defines the format of content in a document. If a schema is included, the protocol validates that every update conforms to the schema and will discard malformed updates. Tags are a set of keywords that allow documents to be categorized and contextualized within the network. They are especially useful when indexing or searching for documents.

#### 2.1.8 Backup
External third-party data persistence. Documents may specify one or more backup services for persisting content beyond the node. Document content will always be pinned locally on the node using IPFS, but oftentimes additional storge guarantees are useful.

### 2.2 Peer-to-Peer Network
The Ceramic Network is a trusted, peer-to-peer, dynamic information management platform for building next-generation decentralied applications. The Ceramic network has been designed from the ground up to handle extreme scale, be customizable, ensure trust, Ceramic aims to provide the permissionless content management infrastructure upon which a trusted, worldwide content ecosystem can be built. By liberating dynamic content management from centralized servers, the Ceramic network can act as the decentralized discovery and state management layer that adds trust to our collective content online. Because participants can create and resolve documents for any type of information without any centralized service, Ceramic unlocks interoperability between *all platforms and services across the web*. Ceramic is ideal for storing information that requires guaranteed trust, cross-platform interoperability, and multi-party consumption. Ceramic is the trusted foundation upon which a more connected, transparent, and user-centric internet is built. Worldwide content ecosystem.

#### 2.2.1 Ceramic Nodes
Ceramic nodes run the Ceramic protocol and are responsible for managing documents, orchestrating backups and anchoring, gossiping updates, and responding to queries for a given set of documents which it cares about. Anyone can run a node to manage their own set of documents, or the documents of many users.

##### 2.2.1.1 Ceramic Node Functions

**Validate updates**: Schema validation, state transition rules specified by the doctype. **Pin content**: DID authorship. Ceramic doens't provide a locked-in account model. **Pin state**: DID authorship. Ceramic doens't provide a locked-in account model. **Gossip updates**: Gossip updates to documents with other nodes using libp2p. **Respond to queries**: Add description.***Delegate anchors*** Documents can optionally define a schema. If a schema is defined, nodes will validate that every update made to the document conforms to its schema and will discard malformed updates. **Orchestrate backups**: Every document must specify a doctype, which is its smart engine. Doctypes describe the rules for content and logic for state transitions. Doctype rules are enforced by nodes every time updates are made to the document. **Execute hooks**: Add description

##### 2.2.1.2 Ceramic Node Configurations

In order for nodes to perform these functions, they need to be configured. Ceramic nodes are extremely flexible and configurable. Because there is no global state on Ceramic, node operators need to configure their node to perform actions in a certain way based on the users, functionality, and use cases they desire to service. **Doctypes**: A set of doctypes that this node is capable of interacting with. Doctypes are packages that must be installed when the node is instantiated. Nodes come with three pre-installed doctypes: [Tile (CIP-N)](), [3ID (CIP-6)](), and [Account Link (CIP-N)](). **DocIds**: A list of documents that this node is responsible for watching and pinning. **Anchor services**: A list of blockchain anchor services to which this node may forward valid updates for finalization. Each anchor service may differentiate according to chain, frequency, cost, etc. **Backup services**: A list of backup services to which this node may forward content for redundant storage. **Hooks**: A set of micro-programs that this node is capable of interacting with. Hooks are packages that must be installed when the node is instantiated.

Ceramic can be run directly in-browser using ceramic-core, or it can be run remotely in Node.js and connected to via an HTTP API. The Ceramic monorepo containing both implementations can be found at [ceramicnetwork/js-ceramic](https://github.com/ceramicnetwork/js-ceramic).

#### 2.2.2 Libp2p: Gossip Protocol for Document Replication and Queries

[Libp2p]() is a gossip networking protocol for that is used by Ceramic nodes for document replication and queries.

Data replication / network activity events and updates

Queries

#### 2.2.3 Wallets


##### 2.2.3.1 DID-Based Account Model
Ceramic 

##### 2.2.3.2 DID Provider Interface


## 3. Use Cases
As a general purpose platform for building decentralized applications and infrastructure, Ceramic can support an extremely diverse set of use cases. Most production systems and applications that use Ceramic will combine these simple primitives (DIDs, account links, and tiles) to enjoy the simplicity, interoperability, and scale that is only possible when identities, resources, and services are unbundled from application silos. Here are a few powerful use cases that are built on Ceramic:

### 3.1 Decentralized Identity Management
Ceramic can be used as a platform for complete decentralized identity management.

#### 3.1.1 Decentralized Identifiiers (DIDs)
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

#### 3.1.2 Decentralized Identity Indexes
Identity-centric web, provide context, capability, and meaning for a DID. Resource discovery, routing. Content routing.
*See [Identity Index (IDX) (CIP-11)]() for an example of how Ceramic documents can be used to construct an identity index.*

#### 3.1.3 Verifiable Claims Management
Store claims content in the network, or alternatively to use the network as a state management system for claims where documents are used to verify the current state of claims and handle revocation.

#### 3.1.4 Portable Social Graphs
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

#### 3.1.5 Portable Profiles
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

#### 3.1.6 Linked Accounts
Decentralized keybase. domains, social accounts, *See [Accounts Index (CIP-N)]() for an example of how Ceramic documents can be used as a directory of linked accounts.* Account links are verifiable public mappings that allow a DID to prove that it owns a different public cryptographic identity that is also capable of signing, such as a public key, smart contract, or other DID.

#### 3.1.7 Key Management
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.* *See [Auth Keychain (CIP-N)]() for an example of how Ceramic documents can be used as a DID keychain.*

#### 3.1.8 Data Collections
Collections Indes, Collection Definitions, Collection References, --Routing, very related to the identity index described above. DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

### 3.2. Discoverable and Shareable Schemas
Ceramic documents are great for managing schemas in the public context where they can easily be discovered and reused by others. Because documents have referencable versions, you can choose to utilize a specific version of a schema without worrying about the schema changing while using it.

### 3.3. User-Managed Access Control Systems
There are many ways that Ceramic documents can be used as access controllers for other resources; a few examples: Store user-managed access control lists for a given resource, which can be checked by a service provider prior to permitting access.; Store various access control keys (write, read, follow, etc) to other resources encrypted inside documents, which allows the user to share those keys with others upon request.

### 3.4. Application User Registries
Applications can create documents which store their user table and can also do things like permit users to register a new username. To do this, your application would need to create a DID and operate a microservice which manages your app's key. 

### 3.5 Public Content Publishing
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

### 3.6 Websites & Content Management Systems (CMS)
DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

### 3.7 Social Media Content Storage
Store social media content such as 1, 2, 3, 4, 5, and more in the public domain instead of your applications server. A few benefits of storing this content on Ceramic: Users can update/edit their content at anytime, Content can be shared across platforms, Content can be added to their Identity Index, to enable identity-centric cross-platform discoverability.

### 3.8 User and Application Data Storage
User data, application data. Public or private. DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*

### 3.9 Discoverable Service Definitions
Publish public API and service definitions. DIDs are globally-unique identifiers that can sign/encrypt information, authorize access to resources, and interact various services and data online. DIDs may be used to represent users, organizations, applications, services, devices, etc. *See [3ID (CIP-6)]() for an example of how Ceramic documents can be used to create DIDs.*


## 4. Building
You can start building today on the Clay devnet. Fire mainnet should be released mid-Q4 of this year (2020).
The Ceramic monorepo is available at [ceramicnetwork/js-ceramic]().
Ceramic is available in two. JavaScript node ceramic-core which can be run in-browser or on node.js. If it is run remotely in node.js, users can communicate with thix remote node using an HTTP API. Also available as a CLI, which is useful when developing with Ceramic or creating documents for your application.
Tutorial

## 5. Contributing
Issues: Bugs and issues with code. Create new issues directly in the affected repository.
CIPs: Propose Improvements, standards, and use cases - such as new doctypes, etc.
CEA: Working groups - join the CEA
Community: Call Calendar - Community Calls, Core Devs Calls; Discord - Community and Developer Chat; Twitter - Social; 

## 6. Continue Reading

### [Ceramic Technical Specification  >](https://github.com/ceramicnetwork/specs)

----

## Appendix

### Figure 1. Technology Comparisons
Let's examine Ceramic compared to a few popular alternatives.
| Feature | Ceramic | IPFS | Filecoin | ThreadsDB | Traditional DB | ETH Registry | OrbitDB | Arweave |
| ------- | ----------- | ---------- | ---- | ---- | ---- | ---- | ---- | ---- |
| *Unit* | **Smart document** | File | File | Database | Database | Smart contract | Database | Transaction |
| *Content ID* | **DocId** | CID | CID | DBID | HTTP Endpoint | Address | DBID | Transaction |
| *Data Format* | **IPLD** | IPLD | IPLD | IPLD | N/A | Transaction | IPLD | Transaction |
| *Data Persistence* | **Configurable** | Hosted | Decentralized | Configurable | Hosted | Decentralized | Hosted | Decentralized |
| *Mutable* | ✅ | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ | ❌ |
| *Ordering* | **Strict** | NA/ | N/A | CRDT | Variable | Strict | CRDT | Strict |
| *State Persistence* | **Decentralized** | N/A | N/A | Federated | Centralized | Decentralized | Federated | N/A |
| *Programability* | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ |
| *User Model* | **DIDs** | N/A | Filecoin Key | DB Key | Server Auth | Blockchain Key | DB Key | Arweave Key |
| *Discovery* | **Public** | Public | Public | Private | Private | Public | Private | Public |
| *Network* | **P2P** | P2P | P2P | Federated | N/A | P2P | Federated | P2P |


</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
</br>
-----
-----


## Ceramic Overview

[**Ceramic**](http://ceramic.network) is a permissionless protocol for creating and accessing mutable, tamper-proof documents that serve as the foundation for a web without silos. Ceramic's infrastructure provides a verifiable, censorship-resistant source of truth for important information that is public and interoperable. By migrating critical information from isolated servers into the public commons governed by digital signatures and consensus, Ceramic enables users and applications to break free from information and infrastructure silos, and enables developers to build in a composable and efficient manner. Ceramic does for identities, data, and services what blockchains have done for assets. 

Because participants can create and resolve documents for any type of information without any centralized service, Ceramic unlocks interoperability between *all platforms and services across the web*. Ceramic is ideal for storing information that requires guaranteed trust, cross-platform interoperability, and multi-party consumption. This makes Ceramic perfect for storing decentralized identifiers and their associated metadata, policies for usage of services, access control permissions, data schemas, and other documents that collectively enable wallets and applications to access a dynamic and unbundled ecosystem of interoperable identities, databases, and services. Ceramic enables: 

- [Portable, self-sovereign identity](#portable-self-sovereign-identity)
- [Interoperable user and application data](#interoperable-data-ecosystems)
- [Open web services, without new accounts or logins](#open-web-services)

> For more information, jump directly to [use cases](#use-cases) or view [examples](#examples).

Ceramic's global ecosystem of interoperable resources allows developers to build composable applications with unprecedented modularity, trust, and scale. Ceramic is the trusted foundation upon which a more connected, transparent, and user-centric internet is built.

### Background

Despite the benefits of cloud services, SaaS tools, and API businesses, building a fully featured product or service is still extremely complex, fragile, and limited. Even simple apps require deploying and maintaining a backend, securing and managing user identities and data, and tying together a tangle of APIs and services. Choices made early often lock developers in to long term relationships with technology providers, which vendors exploit. Making a product's value-add interoperate with other products and services is often difficult and unpredictable. All of this is because infrastructure, information, and access control are needlessly replicated and siloed for each individual application. 

To combat these problems of duplication, fragmention, and insecurity, the internet needs a flexible public infrastructure where participants can store verifiable information that is universally discoverable and accessable across all applications. By keeping identifiers, their associated data, and services in the public domain instead of on siloed application servers, they can be accessed by all participants across the web. In this model, participants directly define and control their resources, share (or not) these resources with others, and bring their identities and metadata across experiences. 

In addition to giving users more agency and control, this model dramatically simplies the experience for developers as well. Instead of spending effort on managing data and tying together various services, developers can focus on the value-add in their product. Each application can simply query an identity for the information and access they need. Data can be easily shared across products without compromising privacy. Experiences can be composed in real-time to a users preferences. Bilateral account signups and agreements can be done away with, replaced instead by frictionless payment channels for services.

All of this frees products and services from needing to perform non-critical functions, reconciling services and data, worrying about user trust and liability, or scrambling to attract and retain users through many points of friction. Instead, developers can simply build a product that plugs into an already existing ecosystem of users, data, and services that work seamlessly together. Over time, this will result in more targeted mircoservices and microapplications being developed, instead of the behemoths we see today.

### Requirements
The composable web needs a permissionless, identity-centric interoperability protocol to provide applications with all the information they need to easily discover, route to, gain access to, and interact with a user's resources regardless of which wallet users bring, which applications created the data, or where the resources are located. This protocol must: 

1. Permissionlessly register an interoperable identity (DID); 
2. Privately control this identity with multiple private keys;
3. Publicly associate public keys and accounts to this identity;
4. Publicly or privately associate resources to this identity;
5. Set permissions for resources;
6. Perform access control to resources;
7. Interoperably sign and/or encrypt information; and
8. Revoke private keys, public keys, and permissions for resources. 
 
In addition to these base requirements, a protocol aiming to unlock interoperability should also allow applications and services to:

9. Publish metadata and definitions;
10. Publish data schemas; and
11. Publish policies and service agreements.

Finally, a solution aiming to make it simpler to build powerful applications must be easy for developers to use. It must fit with existing mental and development models, add no additional burdens, and scale well with new use cases and complexity.

## Ceramic Documents

Ceramic provides a *universal graph of verifiable documents*. Ceramic documents are signed, append-only objects stored in [IPFS](https://github.com/ipfs/ipfs), encoded using [IPLD](https://github.com/ipld/ipld), and anchored in one or more blockchains. Due to its hybrid design relying on IPFS/IPLD and various blockchains, Ceramic's document graph is interoperable, scalable, permissionless, and low cost (variable depending on blockchain anchor service). 

Documents are a flexible primitive that can be modeled to represent many things, however each document must conform to a specific *doctype* supported by the protocol. Doctypes specify rules that govern what is a valid update to the document such as signatures and state transitions. This allows Ceramic nodes to verify the state of a given document in a decentralized way.

Ceramic currently supports three standard [doctypes](https://github.com/ceramicnetwork/specs#document-types): [3ID](#decentralized-identifiers-dids), [account-link](#account-links), and [tile](#tiles). Below, find some of the common ways that these doctypes are used. If your use case doesn't fit into one of these doctypes, you can add new doctypes to the protocol by submitting an issue on the [Ceramic specs](http://github.com/ceramicnetwork/specs/issues) repository.

>Learn more about [Ceramic documents](https://github.com/ceramicnetwork/specs/blob/master/README.md#protocol-overview).

### Decentralized Identifiers (DIDs)

DIDs are globally unique identities used to sign documents on the Ceramic network and also interact with arbitrary off-chain services and data. More specifically, they are abstract, key-agnostic interfaces used to uniquely identify entities, interoperably sign and encrypt information, authorize authentication/access control to services, and store mappings to additional resources. Ceramic makes no assumptions about what kind of entity a DID represents, so they can be users, organizations, applications, services, devices, etc. DIDs can be controlled by one or many private keys, providing flexibility and interoperability across wallets and platforms. 

#### 3ID Identity

The first and most widely used DID method on Ceramic is 3ID. More than 15,000 3IDs are already being used in production. Other DID methods that conform to the [W3C DID spec](https://www.w3.org/TR/did-core/) may be added to the network as additional doctypes. 

> Learn more about [3IDs](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md) or see an [example](https://github.com/ceramicnetwork/specs/blob/master/doctypes/3id.md#example). 

### Account Links

Account links are the second doctype supported by Ceramic. Account links are verifiable public mappings that allow a DID to prove that it owns a different public cryptographic identity that is also capable of signing, such as a public key, smart contract, or other DID.

> Learn more about [account links](https://github.com/ceramicnetwork/specs/blob/master/doctypes/account-link.md).

### Tiles

Tiles, the third doctype supported by Ceramic, are the most general form of a document and can be used to represent almost any kind of information. Tiles are a way to make verifiable statements by one or more DIDs. Tiles may act as standalone objects or they can reference other tiles. This allows for composability between various tiles, creating a relational graph of verifiable, mutable information. See below for a few examples of how tiles will be used on Ceramic.

> Learn more about [tiles](https://github.com/ceramicnetwork/specs/blob/master/doctypes/tile.md).

#### Schemas

The first use case for tiles is creating verifiable, globally-available data schemas. Schema tiles allow a user to define a canonical schema that can be used by anyone anywhere in the world, encouraging multiple parties to converge around standard schemas. This makes schema tiles valuable in their own right. Schema tiles are also used to provide structure to information contained in other tiles. Because of this, schema tiles are the core building block for other tiles, such as those below. Schemas tiles can be thought of as templates for other tiles.

#### Metadata

Tiles are used to express additional metadata or context about Ceramic DIDs. At a minimum, DIDs need a DID Manager tile so they can be controlled by one or more private keys. Other metadata needs will vary depending on the type of entity that a DID represents and the use case.

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

Tiles are used to define more explicit, specific terms around the design of a particular service or the access control requirements and permissions needed to access it. For example, policies can define the data model for an application, terms and requirements of a service, or the permissions set by a user to access their data.

- **Collection Policy**: Used to define an app's data model (database types plus references to schema tiles)
- **Service Policy**: ToS and requirements for using a resource, may include service endpoint and payment info
- **Privacy Policy**: User-managed access control permissions to their resources

#### Agreements

Tiles are used to form explicit agreements between DIDs. An example of this would be a **Service Agreement**, which is a multi-party agreement between a provider and purchaser of a service (i.e. data hosting).

#### Claims

Tiles are used to create statements about other DIDs. To achieve this they can create a **Verifiable Claim**, which is a flexible standard for creating signed statements or data. If the verifiable claim is accepted by the recipient, is included in the recipient's metadata above.

## Use Cases

Most production systems and applications that use Ceramic will combine these simple primitives (DIDs, account links, and tiles) to enjoy the simplicity, interoperability, and scale that is only possible when identities, resources, and services are unbundled from application silos. Here are a few powerful use cases that are built on Ceramic: 

### Portable, Self-Sovereign Identity

Self-sovereign identity (SSI) describes a system where participants can permissionlessly create and control their digital identity using one or more private keys. Technically, SSI could be enabled by any decentralized asymmetric cryptography system where public keys (identities) are controlled by private keys (passwords) such as bitcoin or ethereum. However, this type of system would be limited to the network on which these identities are registered, as well as the single private key account. These two constraints function as silos that prevent this identity from being used interoperably in additional contexts.

For identities to be truly flexible and portable across platforms and keys, which makes them more useful in practice, we need an additional identity abstraction that lives at a layer above blockchain accounts. This is the value of DIDs. On Ceramic, DIDs function as the global public identity and they can be controlled by any number of private keys from any blockchain or cryptographic system. DIDs provide a single interface that owners can use to identify themselves, interoperably sign messages, encrypt data, and auhorize/access control to off-chain services that is agnostic to which blockchain a user is on. DIDs are the antidote to private key and network lock-in.

SSI is often meant to include much more than direct control of an identifier. Most times, this identifier needs more context so others can interact with it, such as profile details. Ceramic tiles allow DID owners to add metadata and additional information or resources to their SSI, making for a flexible and dynamic SSI solution. 


### Interoperable Data Ecosystems

For powerful interoperable experiences, data portability across applications is required. This requires a few core functionalities. First, we need to have a universal way for users to identify themselves across platforms, so that we can know which data is theirs. This is handled by SSI/DIDs (see above). Second, we need to know where this data lives in order to request it. Third, we need to be able to access this data, with users' permission. Last, we need to know the schema of the data so we can consume it in our application without manual processing.

Ceramic makes this simple for all parties. By storing mappings to data resources in a user's DID, Ceramic provides a way for applications (and other data consumers) to efficiently discover where information lives, whether on a specific server or a public network. Also by allowing Ceramic DIDs to define access control policies for their data resources via tiles, Ceramic provides an identity-centric way for users to provide consumers access to their information regardless of where it lives. Instead of access control happening on the server, it happens directly on the user. Finally, Ceramic allows applications to define schemas for any data being saved so that data consumers can know a priori the shape of the data that will be returned, even if it is encrypted.

Together these capabilities allow users to frictionlessly control and share their data across various applications, while also allowing developers to make use of a richer, higher quality dataset than ever - without storing any of it. 

### Open Web Services

The last piece of the interoperability puzzle is providing more open access to web services. All service providers on Ceramic (i.e. data hosting, indexing, anchoring, payments, or other arbitrary web/API services) can service requests from *all* other identities, with no need for bilateral, one-off accounts. Service providers can remove the requirement of creating an account and using an API key to access their service. Rather than through an API key living on an application's backend, services can be accessed whenever a user, application, or other service meets certain pre-defined conditions. This allows service providers to remove all friction from accessing their services and to grow their customer base on a per-use (or other predefined) basis.

For example, a service provider that is hosting user data that needs to be accessed by many different parties can now serve all of them without each of them needing an account with the service. Using Ceramic, the data hosting service can define their service and create a service policy that includes the requirements a consumer must meet in order to access their service. When a user (or application) chooses to use this service to host their data in a database that is access controlled by a Ceramic DID, the user (or app) then adds this resource to their DID. When other consumers want to request this information they need to request access permissions from the user, and once approved, then fulfill the requirments of the hosting service (such as payments or other) before the data will be returned.

Although Ceramic provides the information required for services to accept per-use payments from all parties, the Ceramic protocol itself does not handle payments. Because these transactions will likely be small micropayments, Ceramic is extremely complementary to emerging permissionless cryptographic micropayment networks such as [Connext Network](https://github.com/ConnextProject) on EVM blockchains and [Lightning Network](https://github.com/lightningnetwork/lnd) on Bitcoin. In the most permissionless version of these systems, service providers and end users would run payment nodes and transact. In more practical versions, these responsibilities can be delegated to a third-payment payment processor. This model would also allow applications to pay for services on behalf of their users. We think this make the most sense in the near term.

> Although this example depicts a data hosting service, Ceramic service policies can be used for almost any type of service.

### Examples
To make everything more concrete, let's dive into how [3Box](http://github.com/3box/3box) relies on Ceramic to enable an interoperable, user-controlled data management system. 3Box is a framework that allows developers to store user and application data on a network of open data hosting services access controlled by users instead of on siloed application servers. Users are always in control of their data and can choose to permission it out to other applications, making it shareable across platforms and applications. To achieve this 3Box relies on [self-sovereign identity](#portable-self-sovereign-identity), [interoperable data](#interoperable-data-ecosystems), and [open web services](#open-web-services). 

For self-sovereign identity and to enable user-managed access control, 3Box uses Ceramic's 3ID DID method which allows users to control their identity, information, and services using all of their existing private wallet keys. To enable interoperable data and shared access web services, 3Box relies on the following set of tiles which are created by the various participants that play a role in the system including applications, services, and users:

| Tile | Description | Function |
| --------------- | ----------- | -------- |
| [Schema(s)]() | Describes a data schema used in a partcicular database | Allows *developers* to define their data schemas, or use existing ones |
| [Collection Policy]() | Describes a collection of databases. Links to Schema tiles | Allows *applications* to define their databases and the data models they use so others can easily consume the data |
| [Service Policy]() | Describes simple functions that take an input and produce an output. In this case, it's used for hosting of databases in the Collection Policy | Allows *service providers* to define their service or API and the requirements to access it |
| [Privacy Policy]() | Describes user-managed access control rights to databases in the Collection Policy  | Allows *users* to set permissions and control their privacy while sharing data across apps |

This collection of functionalities allows App A to store data for User B on a hosting service in databases that are access controlled by User B's 3ID. User B can now go to App C and give them permission to access their data from App A. To receive the data from the hosting service, App C must meet the requirements defined by the hosting service's service policy which may include payment information.

## Ceramic Ecosystem

By now you understand that Ceramic enables the emergence of a diverse, interoperable ecosystem of user-controlled wallets, data stores, and infrastructure services that allow developers to build lightweight, composable, collaborative applications. Here's how you can participate.

### Wallets and Authentication Systems

**Integrate Platform-Agnostic, Self-Sovereign Identity**: Give your wallet's users the ability manage their data and other off-chain services using their DID instead of a particular private key. DIDs are an abstraction from individual key pair and contract accounts that eliminate private key lock-in. DIDs are used for interoperable data signing, encryption, and service authorization with all the wallet keys your users already have.

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


