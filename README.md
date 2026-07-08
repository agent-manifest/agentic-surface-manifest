# Agentic Surface Research

**Status: Research incubation.**
**This repository does not contain a specification.**

Nothing here is normative, stable, or ready for adoption.

This repository investigates one question:

> How should digital services declare the terms under which AI agents may invoke them at runtime — and should that declaration become part of an existing standard or require something new?

The answer is intentionally unknown.

Evidence, not prior assumptions, determines the outcome.

---

## Why this repository exists

Modern AI systems increasingly invoke external services at runtime:

- APIs
- MCP servers
- machine-readable tools
- transactional web interfaces
- other digital resources

From the provider's perspective, an important question emerges:

> What should a service be able to declare about automated runtime invocation?

Examples include:

- whether automated invocation is allowed, restricted, or disallowed;
- how inputs are handled;
- who is responsible for the service;
- how access may be revoked;
- what governance information should be available to consumers.

Whether these declarations belong in a new specification—or inside existing standards—is precisely what this repository investigates.

---

## Research scope

Current work focuses on:

- the provider-side perspective of agentic interaction;
- existing standards and protocols;
- identification of genuine gaps, if any;
- vocabulary that could be contributed to existing ecosystems.

The repository deliberately starts from the assumption that **no new standard should be created unless existing standards are demonstrably insufficient.**

---

## Prior art under review

Research currently evaluates work including:

- IETF AIPREF
- TDM Reservation Protocol (TDMRep)
- W3C ODRL
- Model Context Protocol (MCP)
- robots.txt and RFC 9309
- AI-era robots extensions
- A2A Agent Cards
- identity and credential frameworks

The objective is to understand what already exists before proposing anything new.

---

## Possible outcomes

This research may ultimately produce:

- a proposal to an existing standard;
- a profile of an existing specification;
- a vocabulary contribution;
- recommendations only;
- or no new specification at all.

No outcome is predetermined.

---

## Relationship to Agent Manifest

Agent Manifest studies declarations made by autonomous actors.

This repository investigates the declaration needs of digital resources consumed by those actors.

Whether those concerns deserve their own artifact—or belong inside existing standards—remains an open research question.

---

## Current contents

- research notes
- prior-art analysis
- gap analysis
- candidate vocabulary (non-normative)

---

## License

Documentation and research material are licensed under CC BY 4.0.

Any future schemas, examples, or tooling will be licensed under Apache-2.0.

---

## Contact

Hernán Alfredo Capucci

https://agent-manifest-spec.org

ORCID: 0009-0008-7216-3032
