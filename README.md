![ceramic banner](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5f84620b52384d9ec5011a03_ceramicghheader.png)

# Ceramic: The Dataweb for Open Apps
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![](https://img.shields.io/badge/Chat%20on-Discord-orange.svg?style=flat)](https://discord.gg/6VRZpGP)
[![Twitter](https://img.shields.io/twitter/follow/ceramicnetwork?label=Follow&style=social)](https://twitter.com/ceramicnetwork) 

[**Ceramic**](http://ceramic.network) is a global, general purpose, document-based data storage network for securely publishing, linking, and querying verifiable information on the public internet.


### Build with Ceramic

*The Clay devnet is now live for experimentation.* To get started, visit [`ceramicnetwork/js-ceramic`](https://github.com/ceramicnetwork/js-ceramic). This monorepo contains everything you need to build with the TypeScript/JavaScript client either directly in-browser or server-side over an HTTP API.


### Join the community

- **Chat**: Join the [Ceramic Discord](https://discord.gg/6VRZpGP) for questions and discussions.
- **Calendar**: Add the [Ceramic calendar](https://calendar.google.com/calendar/b/3?cid=Y2VyYW1pYy5uZXR3b3JrX3JsNzFrcXZtNzE4ZGY4aWk2cDZzanNmbDdjQGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20) to attend Community Calls and Core Devs Calls.
- **Twitter**: Follow [@ceramicnetwork](http://twitter.com/ceramicnetwork) for official updates.
- **Newsletter**: Subscribe to the [Ceramic Neweletter](http://ceramic.network) to receive recaps of activity.
- **Youtube**: Watch official videos and developer content from the core team on our [Youtube channel](https://www.youtube.com/channel/UCgCLq5dx7sX-yUrrEbtYqVw).


## Moving the world's data beyond the cloud. 

The internet wasn’t built with a native data layer. HTTP database servers have centralized information and power amongst a few Big Tech institutions and resulted in a web of silos rather than a web of data.From decentralized identity to censorship-resistant social media and cross-platform collaboration, many new use cases require a solution for managing dynamic data on the open internet, beyond the control of any single DB server. By combining DIDs, IPFS, blockchains, and p2p networking, Ceramic provides a secure, collaborative, global network for managing user and app data beyond the cloud.

> Learn more by reading the full [Ceramic Introduction](https://github.com/ceramicnetwork/ceramic/blob/master/OVERVIEW.md).


## Smart Document Graph

Smart documents are the most powerful way to manage information on the open web. Ceramic stores data in a graph of JSON-like documents on a public, permissionless network. Smart documents are an extremely general-purpose way to model and consume data that also enables the programmability of information.

**Rich JSON documents**
- Store data as JSON documents like a NoSQL DB
- Set metadata such as owners and tags
- Create separate documents for JSON schemas and reference the schema inside your document. Schemas are automatically enforced by the protocol.

**Programmable smart logic**
- Define custom rules for state transitions to enforce who, how, and when your document is updated without centralized servers. Rules can react to direct events such as a signature from the owner, or indirect events such as an update in another document.
- Hooks can invoke external code or business logic

**Linked content graph**
- Access a worldwide graph of linked information
- Build relationships between Ceramic documents by referencing the `DocID` of other documents
- Use Ceramic documents as a metadata, discovery, and routing layer for off-network data by publishing schemas, definitions, and endpoints

**Strong security and verifiability**
- Documents are immutable, append-only logs of linked IPFS records that are signed by the owner’s DID for verifiability and anchored in a blockchain for strict ordering.
- Documents are identified by a `DocID`, which never changes. DocIDs are deterministically generated from the hash of the genesis record.
- Record content can be backed up to any type of data warehouse, such as decentralized storage (i.e. Filecoin) or cloud databases (i.e. SQL server).

**Flexible deployment options**
- Run Ceramic on the cloud or locally in-browser
- Backup data to any decentralized storage network or cloud database
- Timestamp document updates in any blockchain
- Install plugins for node extensibility

> Read the full [Ceramic Technical Specification](https://github.com/ceramicnetwork/specs).


## Store your most critical data natively on the internet.

**Decentralized identity network:** Ceramic can be used as a flexible, cross-platform decentralized identity graph complete with DIDs, identity metadata such as profiles, linked crypto and social accounts, following lists, user data indexes, and much more.

**Data storage backend:** Improve information security, ship faster, and eliminate the need to configure and run database servers for storing user and application data. Ceramic documents offer capabilities similar to your favorite NoSQL document store.

**Trusted media and content publishing:** From blog posts and social media to media files, Ceramic provides a public infrastructure for publishing content where it can be discovered, versions can be managed, authorship can be verified, and links never change.

**Schema management:** Create a single source of truth for schemas, dictionaries, and other shared definitions in a trusted public context where the information can be discovered by anyone, versions can be managed, and no server is required.


## Collaborate on a global scale.
Ceramic’s verifiable dataweb brings discoverability, integrity, and composability to the world’s information. Openly join the network to publish information and access a vast amount of data resources to use when building your product.

- **Global discoverability:** Discover and access a world of information resources on one global network.
- **Single source of truth:** Every document has a verifiable and publicly auditable state.
- **Horizontal scalability:** Scale to meet the demands of the world’s data at low cost and high speed.
- **Decentralized network:** Our network is completely censorship-resistant and free of middlemen.
- **Content composability:** Reference and build on existing content in ways not possible with siloed servers.
- **Flexible identity:** Transact using any DID. DIDs work with any crypto wallet or key.


## Contribute

### New clients
Want to work on a Ceramic implementation in another language? [Open an issue](https://github.com/ceramicnetwork/ceramic/issues) in this repository to discuss it with others, find help, and coordinate efforts.

### Report bugs and/or issues
To report a bug or issue, open a Github issue on the affected repository.

### Propose improvements and/or standards 
[Ceramic Improvement Proposals (CIPs)](http://github.com/ceramicnetwork/cip) is a process for proposing improvements to the core Ceramic protocol or use case standards. Create a CIP by opening a new issue in the [`ceramicnetwork/CIP`](https://github.com/ceramicnetwork/CIP/issues) repository.

To propose or contribute other features/improvements that don't fit neatly into the above, such as creating an implementation in another language, open an issue in the [ceramicnetwork/ceramic](http://github.com/ceramicnetwork/ceramic/issues) repository.

### Create or join working groups

The [Ceramic Ecosystem Alliance (CEA)](http://github.com/ceramicnetwork/CEA) is a grassroots organization that allows community members to self-organize into topic-based working groups. These working groups allow members to closely collaborate on important issues and produce meaningful outcomes, often in the form of [CIPs](http://github.com/ceramicnetwork/CIP) with wide buy-in from the community. The CEA meets every two weeks, and individual working groups meet on their own schedule. [Click here](https://github.com/ceramicnetwork/CEA#join-the-cea) to join the CEA and get access to the calendar.

## License
MIT
