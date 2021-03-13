---
hip: <HIP number (this is determined by the HIP editor)>
title: Hedera Name Service
author: H. Bart - hbart.lit@gmail.com
type: Standards Track
category: Service
status: Draft
created: 2021-03-13
discussions-to: <a URL pointing to the official discussion thread>
updated:
requires:
replaces:
superseded-by:
---

## Abstract

The Public Key Infrastructure(PKI) of today is highly centralised with a handful of certificate authorities(CAs) being responsible to validate digital identities(such as domains) by vouching for public keys associated with said identities. This system if highly vulnerable as if any one of the existing list of trusted CAs is compromised so is the entire security of the internet. One solution to this is DNS-based Authentication of Named Entities(DANE) which enables domain owners to store a TSLA record in the Domain Name System(DNS) that defines a contract for how clients can trust a public key is in fact owned by said domain before proceeding to establish a TLS connection. However DANE relies on DNSSEC which relies on a chain of trust akin to that in existing CA PKI as previously mentioned hence is susceptible to similar attacks.

By moving DNS(/w DANE enabled) onto a secure decentralised network such as Hedera security issues resulting from the chain of trust in existing systems are mitigated and if widely adopted would render all existing CAs, DNS stakeholders(ICANN, domain registrars) obsolete.

## Motivation

The Hedera Public Ledger is a secure scalable decentralised ledger making it an ideal candidate to supersede existing centralised DNS and PKI systems. Currently the most secure implementations of these systems rely on a chain of trust which is compromised if at least 1-of-m entities in the chain is compromised. The shortcomings inherent to this chain of trust can be mitigated by being replaced with the aBFT consensus of Hedera, hence in order to compromise even a single DNS Resource Record(RR) an attacker must control at least 1/3 of the consensus vote.

Furthermore, the proposed Hedera Name Service(HNS) excels existing systems by enabling the principal owner/s of a domain registered on HNS the ability to update any of their domain's RR at consensus finality speeds(currently <5 seconds), whereas existing infrastructure takes about 1 day for domain propagation. The effective latency would be higher than this as client browsers making for example domain resolution requests would do so to Hedera Mirror Nodes to reduce unnecessary load on MainNet nodes, hence the effectively latency would be the MainNet latency offset by the time it takes for any given Mirror Node to reflect the latest consensus round HNS updates. Furthermore, Mirror Nodes would respond to requests with a state proof that the client browser would validate either via an HNS browser extension client or the browser's built-in HNS client(assuming browser developers find value in doing so). In addition, any other operations facilitated by HNS such as domain atomic swaps or transfers would also be executed at such speeds, which again is orders of magnitude faster than existing systems that can take up to 7 days to process a domain transfer.

## Rationale

The Hedera Name Service offers numerous benefits to both domain users and end users over existing centralised systems. It enables domain owners to:
* near instantly update their domains DNS RR, which includes A/AAAA records for increasing website uptime and enabling censorship resistance amongst other use cases, and TLSA records for near instant approval/revocation of TLS public keys/certificates,
* near instantly transfer or trade domains via atomic swaps, and
* add multisig control of a domain for enhanced security.

Besides the mutual security benefits shared by both domain owners and their respective clients, other potential benefits include:
* the ability for clients to issue payments directly to a given domain owner's wallet, by specifying the domain name in the transaction address field as opposed to the Hedera Hashgraph address alias, as the latter isn't as user friendly as a human readable string. 

## Specification

The technical specification should describe the syntax and semantics of any new features. The specification should be detailed enough to allow competing, interoperable implementations for at least the current Hedera ecosystem.

## Backwards Compatibility

All HIPs that introduce backward incompatibilities must include a section describing these incompatibilities and their severity. The HIP must explain how the author proposes to deal with these incompatibilities. HIP submissions without a sufficient backward compatibility treatise may be rejected outright.

## Security Implications

If there are security concerns in relation to the HIP, those concerns should be explicitly addressed to make sure reviewers of the HIP are aware of them.

## How to Teach This

For a HIP that adds new functionality or changes interface behaviors, it is helpful to include a section on how to teach users, new and experienced, how to apply the HIP to their work.

## Reference Implementation

The reference implementation must be complete before any HIP is given the status of “Final”. The final implementation must include test code and documentation.

## Rejected Ideas

Throughout the discussion of a HIP, various ideas will be proposed which are not accepted. Those rejected ideas should be recorded along with the reasoning as to why they were rejected. This both helps record the thought process behind the final version of the HIP as well as preventing people from bringing up the same rejected idea again in subsequent discussions.

In a way, this section can be thought of as a breakout section of the Rationale section that focuses specifically on why certain ideas were not ultimately pursued.

## Open Issues

While a HIP is in draft, ideas can come up which warrant further discussion. Those ideas should be recorded so people know that they are being thought about but do not have a concrete resolution. This helps make sure all issues required for the HIP to be ready for consideration are complete and reduces people duplicating prior discussions.

## References

A collections of URLs used as references through the HIP.

## Copyright/license

Each new HIP must be placed under the Apache License, Version 2.0 -- see [LICENSE](LICENSE) or (https://www.apache.org/licenses/LICENSE-2.0)
