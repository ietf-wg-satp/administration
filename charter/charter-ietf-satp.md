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

To begin addressing these challenges, SATP will employ the gateway paradigm as
a means for digital assets to be moved from one network to another through a
standardized asset transfer protocol implemented between peer gateways.

Each gateway represents one digital asset network, and SATP allows
gateways to perform a voluntary transfer of a digital asset from the
origin network to a destination network in such a way that evidence of
the transfer can be verified by a third-party audit in the case of
disputes. Both the origin and destination networks are assumed to
share a common understanding of the digital asset.

There might be several gateways representing the same digital asset
network. It is assumed that the same peer gateways representing the
networks are participating in the entire asset transfer sequence from
the beginning to the end.

A key requirement for transferring assets is ensuring that the digital asset is
valid in one network only at any given time. This means that SATP must ensure
that the properties of atomicity, consistency, isolation, and durability (ACID)
of the underlying networks are satisfied in an asset transfer. Commitments and
rollbacks must be supported in the case of an asset mid-transfer failure.

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

    SATP Architecture: The immediate scope of work for SATP will be a base
    architecture that utilizes the gateway paradigm that ensures a common
    semantic understanding to be shared among the modes of asset transfers,
    data sharing and coordinated asset exchanges. The starting point for the
    architecture document will be draft-hardjono-sat-architecture.

    Secure Asset Transfer Protocol: Concurrent with the development of the SATP
    architecture will be the Secure Asset Transfer Protocol that implements the
    transfer of a digital asset from one gateway to another, satisfying the
    ACID properties.

    SATP Use-Cases: Various real-world use-cases will be collected and
    described succinctly, with the goal of providing the background to the SATP
    work.

SATP will define common identifiers, message flows and payloads for
transferring digital assets. A common terminology will be defined in
the architecture document.

SATP will reuse existing IETF standards for various aspects of the protocol
modes, including but not limited to secure channel establishment (TLS), payload
formats (e.g., JSON, CBOR, ProtoBuf, etc.), digital signature and encryption
(e.g., JOSE, COSE, etc.), digital certificates and tokens (e.g., PKIX, JWT,
etc.), and others. SATP may also reuse existing standards from other
organizations (e.g., W3C with DIDs).

Note that for the protocol to work, agreements will likely be needed
between participating digital asset networks that intend to use SATP;
these legal or other frameworks, along with proof of their proper
implementation, are outside of the scope of the SATP.  This assumption
is akin to how the BGP protocol is frequently run between parties that
have previously agreed to route IP packets.
