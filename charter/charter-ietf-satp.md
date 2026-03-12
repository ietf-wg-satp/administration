# Objective

There is currently an interoperability problem in many digital asset
networks (frequently shortened to "network" below for simplicity),
where assets in one network cannot be easily transferred or exchanged
with assets in another network. The problem is more acute in the case
of private asset networks, where external entities have limited or no
visibility into the state of an asset in the private network.

Examples include regulated digital representations of real-world
private assets, regulated government-issued digital currencies, and
privately issued digital tokens.

The goal of the Secure Asset Transfer Protocol (SATP) working group is
to extend the SATP protocol suite by developing additional standard
protocol components that operate between two peer gateways for the
purpose of transferring or exchanging digital assets between an
originator in an origin network and a beneficiary in a destination
network. The resulting protocols shall remain agnostic with respect to
the type of asset and the type of network in which the asset resides.

# Background

The initial work of the SATP working group produced documents defining
an architecture, a core gateway-to-gateway transfer protocol, and
representative use cases. The initial goal was to support
unidirectional asset transfers with locking, atomic commitment, and
error recovery, while deferring additional capabilities to a later
phase.

The recharter builds directly on this foundation and addresses work
that was previously deferred.

# Working group goals

The SATP working group will extend the protocol suite to address
additional interoperability capabilities identified in the
architecture. This next phase will focus on:

- Specification of the pre-transfer negotiation stage assumed but not
  defined in the core protocol.
- Mechanisms for controlled sharing of state information across
  network boundaries.
- Trusted storage, retrieval, and discovery of protocol artefacts
  required for correct protocol instantiation.
- A formal statement of implementation requirements for gateways and
  networks deploying SATP.
- Development of a threat model for the protocol.
- Extension of the protocol to support secure asset exchange between networks.

The working group will maintain the principles established in the
initial charter: the protocol is gateway-to-gateway; networks are
treated as opaque autonomous systems; the protocol is asset-type and
network-type agnostic; and existing IETF standards will be reused
where possible.



The initial work within the SATP WG produced documents defining an
architecture, a protocol and expected use cases.  The initial goal was
to solve some of the identified initial requirements (such as a
uni-directional transfer that supports locking and error recovery) and
defer other work until later (such as bi-directional transfers,
initial negotiation, and gateway discovery).

The SATP working group will next focus on some of the deferred tasks.
It will concentrate on five new elements of work, listed in the
deliverables below

# Deliverables

The deliverables of the SATP Working Group will be as follows:

- SATP will develop protocol steps for an initial negotiation stage
  ("Phase-0") to establish transfer context and agree protocol
  parameters prior to commencement of the core transfer stages.
- SATP will develop a data sharing mechanism enabling authorised
  entities to obtain a verified "view" into another network for state
  and ownership verification, consistent with the architecture.
- SATP will develop a mechanism for storage, retrieval, and discovery
  of protocol artefacts necessary for correct execution of SATP,
  including gateway identities and asset profiles.
- SATP will develop a specification describing requirements imposed
  upon gateways and associated networks when deploying SATP.
- SATP will develop a threat model for the protocol.
- SATP will develop protocol steps to support secure, atomic asset
  exchange between networks.

SATP will continue to reuse existing IETF standards for secure channel
establishment, payload formats, digital signatures and encryption,
digital certificates and tokens, and related technologies. SATP may
also reuse standards from other organisations where appropriate.

As with the initial charter, agreements between participating digital
asset networks that deploy SATP remain outside the scope of the
working group.

# Relationship with other IETF Working Groups

The Transfer dIGital cREdentialS Securely (TIGRESS) working group
focuses on transferring digital credentials, which is related to but
distinct from SATP’s goals of transferring and exchanging digital
assets. TIGRESS addresses wallet-to-wallet transfers, while SATP
specifies gateway-to-gateway transfers.

The SATP working group will coordinate with TIGRESS and other relevant
working groups to promote reuse of applicable technologies and avoid
duplication of effort.
