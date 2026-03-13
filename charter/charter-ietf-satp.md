# Objective

There is currently an interoperability problem in many digital asset
networks (referred to as "network(s)" below),
where assets in one network cannot be easily transferred or exchanged
with assets in another network. The problem is more acute in the case
of private asset networks, where external entities have limited or no
visibility into the state of an asset in the private network.

Examples of networks include regulated digital representations of
real-world private assets, regulated government-issued digital
currencies, and privately issued digital tokens.

The goal of the Secure Asset Transfer Protocol (SATP) working group is
to extend the SATP protocol suite by developing additional standard
protocol components that operate between two peer gateways for the
purpose of transferring or exchanging digital assets between an
originator in an origin network and a beneficiary in a destination
network. The resulting protocols shall remain agnostic with respect to
the type of asset and the type of network in which the asset resides.

# Background

The SATP working group initially produced documents defining an
architecture, a core gateway-to-gateway transfer protocol, and
representative use cases. The WG's initial goal was to support
unidirectional asset transfers with locking, atomic commitment, and
error recovery, while deferring additional capabilities to a later
phase.  The WG will use this foundation and address this previous
deferred work.

# Working group goals

The SATP working group will extend the protocol suite to address
additional interoperability capabilities identified in the
architecture. This next phase will focus on:

- Specification of the pre-transfer negotiation stage that was assumed
  but not defined in the core protocol.
- Mechanisms for controlled sharing of state information across
  network boundaries.
- Trusted storage, retrieval, and discovery of protocol artifacts
  required for correct protocol instantiation.
- Extensions of the SAT protocol to support bidirectional asset
  exchanges between networks.
- A list of implementation requirements for gateways and networks
  deploying SATP.
- Development of a threat model for the protocol.

The working group will continue to maintain the following principles:
the protocol is gateway-to-gateway; networks are treated as opaque
autonomous systems; the protocol is asset-type and network-type
agnostic; and existing IETF standards will be reused where possible.

# Deliverables

The deliverables of the SATP Working Group will be as follows:

- SATP will develop protocol steps for an initial negotiation stage
  ("Phase-0") to establish transfer context and agreed upon protocol
  parameters prior to commencement of the core transfer stages.
- SATP will develop a data sharing mechanism enabling authorised
  entities to obtain a verified "view" into another network for state
  and ownership verification.
- SATP will develop a mechanism for storage, retrieval, and discovery
  of protocol artifacts necessary for correct execution of SATP,
  including gateway identities and asset profiles.
- SATP will develop protocol steps to support a bidirectional atomic
  asset exchange between networks.
- SATP will develop a specification describing requirements imposed
  upon gateways and associated networks when deploying SATP.
- SATP will develop a threat model for the protocol.

SATP will continue to reuse existing IETF standards for secure channel
establishment, payload formats, digital signatures and encryption,
digital certificates and tokens, and related technologies. SATP may
also reuse standards from other organisations where appropriate.

Additional agreements, such as contractual or legal agreements,
between participating digital asset networks that deploy SATP remain
outside the scope of the working group.

# Relationship with other IETF Working Groups

The Transfer dIGital cREdentialS Securely (TIGRESS) working group
focuses on transferring digital credentials, which is related to but
distinct from SATP’s goals of transferring and exchanging digital
assets. TIGRESS addresses wallet-to-wallet transfers, while SATP
specifies gateway-to-gateway transfers.

The SATP working group will coordinate with TIGRESS and other relevant
working groups to promote reuse of applicable technologies and avoid
duplication of effort.
