# IETF Secure Asset Transfer Protocol (satp) WG
- Date: Tuesday -- 2023-07-25 -- 09:30-11:30 Local
- Room: Continental 4

# AGENDA:

## 5m - Chair Introduction (Wes Hardaker)

- Note takers needed
- IETF document process reminders
- Note: we have a tight timeline -- strict adherence to agenda times
required
- Next interim meeting: 15th August

## 5m - SATP Scope (Claire Facer)

- charter reminder
- (currently) out-of-scope assumptions

## 20m - Updates to draft-ietf-satp-core (Thomas Hardjono)

Note taker: Rafael Belchior

- four main updates to satp-core.
- new message flow diagram available: v19
- first big change is removing the redundant ack-prepare (right after
3.2A v19 of the diagram) because the transfer only involves two
gateways. Upon using a three-phase commit with more than two entities,
we would need the ack-prepare (multiple gateways would state they are
ready to commit with ack-prepare).
- Transfer commence stage is moved from stage 2 to stage 1, because,
logically, it belongs to stage 1 (leaving stage 2 for transactions
against systems other than gateways).
- Signing receipts is done due to legal obligations (standalone evidence
for non-repudiation). Thus, we have steps in SATP where these signs are
explicit.
- Ned asks how the transfer protocol claims and receipts happen. Thomas
refers we need better naming for these phases.
- Yaron asks why a multi-negotiation protocol is needed in SATP. Thomas
answers that we have stage 0 for implementing this multi-negotiation
protocol (out of scope)
- Wes reiterates that this session aims to gather feedback on the
current charter. Wes states that we have a strict charter, so we start
approaching the problem slowly.
- Yogesh asks if both gateways are always available. Thomas refers that
we tackle this problem under session resumption and crash recovery.
- Ned asks if we have a state machine defined for each possible claim.
Thomas answers that defining a state machine for each step could be
beneficial.
- Section 7 now groups claims to belong to asset profile definition and
actors claims. Also contains claims about the gateway and network
characteristics.
- Relevant claims should also include considerations about crash
recovery/session ressumption
- Thomas presented some example claims (e.g., digital_asset_id,
asset_profile_id). Thomas stresses that VASPs must ensure that the
Travel Rule is respected (meaning that users should be identified before
the transfer). These claims need more work.
- Session resumption will be presented in detail by Rafael. Thomas said
that the primary-backup model is used, and there is a defined API for
doing the recovery.
- Architecture draft 01 now matches the message flow diagram. We added a
comparison with ISO 20022, addressing one of the questions from IETF
116. References were updated.
- Future work presented: error types and messages; transfer
initialization claims.


## 15m - Updates to draft-ietf-satp-usecases (Venkatraman Ramakrishna)

Note taker: Rafael Belchior

* Rama will provide updates to use cases, compatibility with standards
and implementation.
* Use cases draft had a related discussion on the mailing list on CBDC
interoperability that enables the movement of assets across
jurisdictions.
* Rama introduced decentralized finance (DeFi), emphasizing that those
encompass transactions not relying on a centralized party. CBDCs were
introduced as a form of tokenized cryptocurrency.
* CBDCs look like a compelling application where SATP could be employed
because CBDCs cannot be managed by a single system or metric, for
performance and requirements reasons (different CBDCs exist). Rama shows
that 23 out of 93 central banks have decided on blockchain-based
infrastructure for implementing CBDCs
* Interoperability would happen across a 2-tier architecture, where
wholesale CBDC networks communicate with retail CBDC networks (and
retail banks between themselves, networks assumed to be heterogeneous)
* Chunchi asks if there is a need for interoperability between CBDC and
other DeFi applications. Chunchi asks if interoperability across DeFi
applications would need SATP. Rama answers that SATP moves assets
between networks, applications and use cases that have a broader
spectrum (at this point, not in the charter). Thomas chimes in and gives
the example of a closed private network with a lot of liquidity. Thomas
refers that to showcase the liquidity on that private network one could
use gateways and SATP to issue a claim attesting the liquidity in the
private network. We are preparing the gateway paradigm for when
private-public interop is needed.
* John asks how CBDCs would work with SATP. Thomas refers the case of
Quant network, where a CBDC is used for settlement, and assets are
transacted across other networks. Claire clarifies that CBDC to CBDC
settlement is a different question from moving and managing liquidity
across CBDCs (out of scope for first version). Wes clarifies that this
use case is more complex than the original charter (where there's an
asset being transferred across ledgers).
* ACTION NEEDED: Wes proposes two options to address the complex use
case that is not being currently addressed by SATP: remove said use case
or put a note saying that is currently out of scope (with missing
requirements that are currently not being worked on).
* Rama recalls the question asked in IETF 116 by John Levine (comparison
with ISO 20022). Rama clarifies that the scope of SATP is defined
narrowly and precisely. SATP serves a different purpose that ISO. It
should leverage existing standards for implementing the full-stack of
SATP. "ISO 20022 and SATP play complementary roles in the digital asset
management ecosystem". Possibly we can leverage the ISO standard for
context negotiation in Stage 0.
* Yaron asks for clarification on the interoperability goals. Rama
refers that we could leverage ISO 20022 in SATP stage 0 for asset
interoperability (leveraging discovery). Wes refers that the SATP is the
negotiation process; the message encoding can have a variety of
implementations (eg ISO) - we still haven't decided which protocol
formats to discuss. Thomas happily asks for contributions :)
* Rama gives updates on the implementation of SATP in Hyperledger Cacti
(namely the relay implementation, more decentralized than the first
open-source implementation)
* Wes refers that a way to standardization is to define one mandatory
encoding, and the others are optional
* Ned states privacy concerns - this is being addressed by the group.

## 20m - Crash Recovery, error codes and session resumption (Rafael
Belchior)

Note taker: Thomas Hardjono

- Gateways may enter faulty states.  Sooner or later they will. Some
faults maybe recoverable. Some errors are recoverable by the gateways,
while some may not.

- To address possible crashes, we need a strong local log mechanism
and a recovery strategy for gateways.

- Each gateway has a Log Storage locally, via a Llog-API. They also
have acces to the ledgers (State-DB).

- The strategy is a Log write-ahead strategy, before carrying-out the
process or operation. AN example is shown in Slide 4. For example,
before executing a step it writes the “intention” into the log.

- Handling crashes – 2 models:  self-healing or primary backup. 

- Non-Critical crash:

    - In the primary backup, the gateways need to pre-determine the backup gateways on both sides.

    - The draft defines a number of crash-related States for a gateway.
The RECOVERY_STATE holds a number of these information parameters
defining the state (see draft).

    - Gateways implement two (2) timers (timeout).  First timeout is when
the gateway G1 (crashed) and G2 is is waiting. The second timeout is
when G1-backup has responded and beginning to resume the session.


- Critical crash: 
    - G1 crashes after sending lock-assertion. G2 responds but gets no
answers from G1.  The same procedure is adopted. G1-backup wakes up
and G2 now sends Recover Update.

- WesH asked about disk losses on the part of G1. In which case there may need to be a roll-back.

- Question from Chunchi Liu:  How to fetch context from the crashed G1 (i.e. state database is lost).

- Rafael responds that the primary backup gets a copy of the states (replicated).

- Question from John Levine: this looks like very complex state
machine. Rafael: yes, we need to develop a formal state machine.

- WesH: there is a new IRTF research group: Usable Formal Methods RG.
They may be looking for use-cases. They want to focus on “usable”.
Rafael did consider tools/models like universal composable model, but
still waiting for this SATP draft to become stable.

- Some topics for group discussion:

- Rollback logic: If an asset has been locked, then a rollback means that it needs to be unlocked.

- Session resumption: should resumption be explicit or implicit.
Also, what happens on timeouts on the recover messages.

- Burn-Mint versus Lock-Unlock: which is safer (due to honeypots). What are the trade-offs.

- Question from Dmitry Vinokurov: how big can the asset be?  Rafael
answers that it is a burn-mint model and depends on the Asset Profile.

- Error schemas: we are developing a Error schema, with types and
descriptions.  This also allows gateway operators to define custom
error message.

- Question Chunchi Liu: Burn-mint may be more dangerous than
lock/unlock.  It could harm the entire system.  Rafael/Thomas answer:
the mechanism isa dependent on the networks.

- There are at least 2 independent implementations of SATP.

- Next steps: error scopes and error types.

- Question from Yaron: there is need to be more text on
security/trust guarantees described in the draft (e.g. attacks
timestamps). Rafael: the decentralized log storage is the current
approach, but we want to look at to other strategies.

- Last comment from Dmitry: we should consider tunnels between
gateways that provide stronger guarantees.




## 10m - Asset profile definition (Denis Avrilionis)

Note taker: Rafael Belchior

* Denis shows a figure depicting the different systems behind a gateway.
Asset profiles created by asset issuers, each instantiation is used by
SATP.
* Denis presents the data requirements of the asset profile (WIP),
negotiated in stage 0. Asset profile should include the capabilities,
including if its burn-able. Asset profile includes considerations about
law enforcement (can it be confiscated?)
* Asset instances have processing requirements: e.g., assets must be
serializable; different RFCs should be used to our purposes.



## AOB - time remaining (45m)

### 20m - Gateway Transfer Initialization Claims (Thomas Hardjono)

- (skipped to give time back to the agenda)

### 10m - stage 0 transfer context negotiation (Denis Avrilionis)

Note taker: Rafael Belchior

* Denis shows an example of a stage 0 flow diagram. Three layers:
Application - gateway - network. Application-to-application
communication happens in stage 0, which executes requests (asset
transfers) from clients. Application creates a transfer context encoding
the request, that is communicated to the other application (that on its
turn communicates with its gateway).
* Session IDs might be related to each other (e.g., session id of a
crashed session + session id with the recovered session).

### 15m - sharing of asset state and process snapshot views (Venkatraman Ramakrishna)

Note taker: Rafael Belchior

* Goal is to understand which parts of the blockchain view to
standardize.
* First use case for views is asset transfers; data transfers and asset
exchanges also exist.
* Data transfers are mostly useful on private networks (because on open
networks all data is visible)
* Thomas gives an example for data transfers: counterparty risk. Idea is
that both sides in a trade are not sure about the other's liquidity.
Centralised market makers solve this problem. In the DeFi world with
private closed networks, you would need evidence for this liquidity.
* Rama gave an overview of cross-network workflows.
* Remote state views are peer-reviewed and have an implementation on
Hyperledger Cacti.
* Views allow a client to build standardized queries and responses
against database/ledger.
* View addresses are descriptors for the queries
* Standardisation efforts for views would be receiving requests for
views  (view address) and responding with view responses.
