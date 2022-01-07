![ceramic banner](https://uploads-ssl.webflow.com/5e4b58d7f08158ece0209bbd/5f84620b52384d9ec5011a03_ceramicghheader.png)

# Ceramic: A decentralized network for mutable information
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://lbesson.mit-license.org/)
[![](https://img.shields.io/badge/Chat%20on-Discord-orange.svg?style=flat)](https://discord.gg/6VRZpGP)
[![Twitter](https://img.shields.io/twitter/follow/ceramicnetwork?label=Follow&style=social)](https://twitter.com/ceramicnetwork) 

[**Ceramic**](http://ceramic.network) is a public, decentralized, censorship-resistant network for managing mutable information on the open internet without databases or servers. In Ceramic all content is stored in smart documents, which are append-only IPFS logs where each commit is signed by a decentralized identifier (DID) for verifiability and then subsequently anchored in a blockchain for consensus. Because Ceramic is built on a completely peer-to-peer network, all documents are openly discoverable and can be referenced by other documents or queried by any other participant on the network. For more information, see the [Ceramic website](https://ceramic.network), the [Ceramic documentation](https://developers.ceramic.network), or try the [demo app](https://playground.ceramic.dev).

> **Project status: Clay testnet is now live.** 🚀</br>`Clay` is a decentralized public network ready for experimental application development and testing. It anchors documents on the Ethereum Ropsten and Rinkeby testnets. It is the last major milestone before `Fire` mainnet, which is under development and will launch in late Q1 or early Q2 2021. Documents published on Clay will *not* be portable to Fire. Read the [full announcement here](https://blog.ceramic.network/ceramic-network-clay-testnet/).

## Smart documents
Smart documents are the most powerful way to manage information on the open web.

- **Mutable documents**: Store information in collections of mutable documents like your favorite NoSQL document database.
- **Immutable identifiers**: Every document gets a globally unique persistent identifier, called a `DocID`. This DocID will never change regardless of how many updates are made to the document.
- **Verifiable signatures**: Every update to a document must be signed by the DID of its owner, providing verifiability to its content.
- **Schema-enforced content**: Documents can have schemas which will be enforced by the protocol. This allows for data integrity and simple cross-platform interoperability.
- **Strict versioning**: Every update made to a document is anchored in a blockchain, so its commits follow a strict order. This allows the protocol to guarantee the state of a document at every commit and allows its content to be auditable and trusted at all times.
- **Programmable logic**: Define custom rules for state transitions to enforce who, how, and when your document is updated without centralized servers. Rules can react to direct events such as a signature from the owner, or indirect events such as an update in another document.
- **Configurable persistence**: Nodes can back up documents to any centralized or decentralized data storage platform.

## Getting started

Here are a few useful links to help you get started with the Ceramic network.

### Development

- See what's possible by trying the [demo application →](https://playground.ceramic.dev)
- Learn the basics by setting up and interacting with the Ceramic CLI. [Quick start guide →](https://developers.ceramic.network/build/quick-start/)
- Full documentation on clients, installation, and usage can be found on the [Ceramic documentation site →](https://developers.ceramic.network/build/installation/)

### Tools
[Ceramic Studio](https://github.com/ceramicstudio) is a community-run Github organization that contains a set of useful tools to use when building with Ceramic. Notably it contains [IDX](https://idx.xyz), a decentralized identity protocol that provides a unified, user-centric alternative to app-specific user tables. IDX allows users to build up a single index of all of their data while enabling developers to break down silos and freely discover and share a users' data between applications. IDX uses Ceramic to store protocol data, but it can be used by applications that store data in any type of datastore, including Ceramic documents.

### Community

- Questions, support, and discussions: [Join the Ceramic Discord](https://chat.ceramic.network)
- Bugs and feature requests: Create an issue on the appropriate Github repository
- Attend community calls and core devs calls: [Add the calendar](https://calendar.google.com/calendar/b/3?cid=Y2VyYW1pYy5uZXR3b3JrX3JsNzFrcXZtNzE4ZGY4aWk2cDZzanNmbDdjQGdyb3VwLmNhbGVuZGFyLmdvb2dsZS5jb20)

### Content

- News and updates: [Follow Ceramic on Twitter](http://twitter.com/ceramicnetwork)
- Content, guides, and tutorials: Check out the [Ceramic Blog](https://blog.ceramic.network)
- Videos: Watch the [Ceramic Youtube channel](https://www.youtube.com/channel/UCgCLq5dx7sX-yUrrEbtYqVw)

## Contributing
We are happy to accept small and large contributions, feel free to submit a pull request.

## License
Ceramic is fully open source and dual-licensed under MIT and Apache 2.
