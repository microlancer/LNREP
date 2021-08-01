# LNREP
LNREP - A draft specification of the LN Reputation and Arbitration Network protocol

## Overview

LNREP defines communication rules between LNREP nodes. Each LNREP node assumes a Lightning Network node exists, and could be implemented as a plugin of the lightning node, or independent daemon. An LNREP is associated to an identity, and the identity is identified by the lightning node's pubkey. The reputation, history, esrow score, etc. are all associated to the node.

## Nodes 

An LNREP-enabled Lightning node can run as:

* Client-only
* Client + Arbitrator

Nodes in the arbitration network can receive income for participating in 2-of-3 (or other n-of-m) multisignature transactions. The job of arbitrators is to assist in resolving disputes, generally following agnostic procedures and code of conduct. Each arbitration node will have a reputation score based on the number of successful dispute resolutions.

Available arbitrators are on a globally public list of nodes willing to arbitrate transactions. Their reputation, number of transactions, size of transactions, public comments, fee rate, etc. are all listed together on the list. 

The transaction participants should agree on an arbitrator. Funds can then be escrowed in two ways:

Short-term:
* HTLC escrow for instantaneous deliveries (e.g. sending an ebook, etc)
* On-chain n-of-m escrow for long-term deliveries (e.g. sending a physical book, etc)

## Cases

An arbitration case is opened when there is a dispute. Both parties submit their case and evidence to the network for evaluation. After a period of collecting information from the parties, each node will submit their opinion on how the case should be resolved. This is done in a voting process, where the opinion is how much of the funds locked in escrow should go to each party in the transaction. In the case of "no opinion" the funds are split 45/45 with the remaining 10% going to the arbitrator(s) as a fee for their time.

## Reputation

For successful transactions, both parties will gain a reputation score, as well as the arbitrator reputation (for responsiveness). For disputes, the arbitrator will receive a more comprehensive reputation score that includes a review from both parties on the outcome. Since it is likely that a dispute makes both parties unhappy with the resolution, this is taken into account with remarks in response to the review. 

