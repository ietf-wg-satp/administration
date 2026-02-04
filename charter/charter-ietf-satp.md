# Objective

There is currently an interoperability problem in many digital asset
networks (frequently shortened to "network" below for simplicity),
where assets in one network cannot be moved easily to another
network. The problem is more acute in the case of private asset
networks, where external entities have no visibility into the state of
an asset in the private network.  An example is regulated digital
representations of real-world private assets, such as property
ownership certificates, and regulated government-issued digital
currencies.

The goal of the Secure Asset Transfer Protocol (SATP) working group
will be to develop a standard protocol which operates between two peer
gateways for the purpose of transferring digital assets between an
originator in the origin network to a beneficiary in a destination
network.  The resulting protocol shall be agnostic with respect to
the type of asset being transferred.

# Problem space and architecture

The initial work within the SATP WG developed documents defining an
architecture, a protocol and some expected use cases.  The initial
goal of the working group was to solve some of the identified initial
requirements (such as a uni-directional transfer that supports locking
and error recovery) and deferred other work until later (such as
bi-directional transfers, initial negotiation, and gateway discovery).
Additionally, during the initial work efforts, the WG identified other
SAT protocol elements that were needed to fulfill the larger goal of
providing an interoperable messaging protocol for transferring digital
assets.

The SATP working group will next take on five new elements of work,
listed in the deliverables below, that provide the SAT protocol with
additional features for supporting more advanced usage.

# Relationship with other IETF Working Groups

The Transfer dIGital cREdentialS Securely (TIGRESS) working group is
focused on transferring digital credentials, which is akin to but not
equal to SATP's goals of transferring digital assets.  An additional
difference is TIGRESS is a wallet-to-wallet transfer, while SATP's
proposed solution involves a gateway-to-gateway transfer. The SATP
working group will work with TIGRESS proponents to ensure reuse of
existing TIGRESS outputs are used within SATP to promote technology
reuse.

# Deliverables

The deliverables of the SATP Working Group will be as follows:

- SATP will develop protocol steps for developing an initial
  negotiation (referred to as "Phase-0").

- SATP will develop a data sharing mechanism so that entities can
  obtain a "view" into another network for state and ownership
  verification, for example.
  
- STAP will develop a registry for negotiating communication
  requirements.
  
- SATP will develop a list of requirements being imposed upon an asset
  network and its gateway when deploying the SAT protocol.
  
- SATP will develop a threat model for the protocol.

SATP will continue to reuse existing IETF standards for various
aspects of the protocol modes, including but not limited to secure
channel establishment (TLS), payload formats (e.g., JSON, CBOR,
ProtoBuf, etc.), digital signature and encryption (e.g., JOSE, COSE,
etc.), digital certificates and tokens (e.g., PKIX, JWT, etc.), and
others. SATP may also reuse existing standards from other
organizations (e.g., W3C with DIDs).

Note that for the protocol to work, agreements will likely be needed
between participating digital asset networks that intend to use SATP;
these legal or other frameworks, along with proof of their proper
implementation, remain outside of the scope of the SATP.  This
assumption is akin to how the BGP protocol is frequently run between
parties that have previously agreed to route IP packets.
