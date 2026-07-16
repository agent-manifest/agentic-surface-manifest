# Agentic Surface Research

**Status: Research incubation.**
**This repository does not contain a specification.**

Nothing here is normative, stable, or ready for adoption.

This repository investigates one question:

> How should digital services declare the terms under which automated reasoning systems may invoke them at runtime—and should those declarations become part of existing standards or require new standardization work?

The answer is intentionally unknown.

Evidence, rather than prior assumptions, determines the outcome.

---

## Why this repository exists

Modern automated systems increasingly invoke external services at runtime:

- APIs
- MCP servers
- machine-readable tools
- transactional web interfaces
- other digital services and interfaces

From the provider's perspective, an important question emerges:

> What should a service be able to declare about automated runtime invocation?

Examples include:

- whether automated invocation is allowed, restricted, or disallowed;
- how submitted inputs are handled;
- who is responsible for the service;
- how access may be revoked;
- what governance information should be available to consumers.

Whether these declarations belong in a new specification—or inside existing standards—is precisely what this repository investigates.

---

## Research scope

Current work focuses on:

- the provider-side perspective of automated service invocation;
- existing standards and protocols;
- identification of genuine gaps, if any;
- candidate vocabulary that could be contributed to existing ecosystems.

The repository deliberately starts from the assumption that **no new standard should be created unless existing standards are demonstrably insufficient.**

---

## Prior art under review

Research currently evaluates work including:

- IETF AIPREF
- TDM Reservation Protocol (TDMRep)
- W3C ODRL
- Model Context Protocol (MCP)
- Robots Exclusion Protocol (RFC 9309)
- AI-related robots extensions
- Agent2Agent (A2A)
- identity and credential frameworks

The objective is to understand what already exists before proposing anything new.

---

## Possible outcomes

This research may ultimately produce:

- a proposal to an existing standard;
- a profile for an existing specification;
- a vocabulary contribution;
- recommendations only;
- or no new specification at all.

No outcome is predetermined.

---

## Relationship to Agent Manifest

Agent Manifest studies declarations made by autonomous actors.

This repository investigates the declaration needs of the services and interfaces consumed by those actors.

Whether those concerns deserve their own artifact—or belong inside existing standards—remains an open research question.

---

## Current contents

- `docs/provider-side-declaration-survey.md`

---

## License

Code is licensed under Apache-2.0 (see `LICENSE`).

Documentation and research material are licensed under CC BY 4.0 (see `LICENSE-DOCS.md`).

---

## Contact

Hernán Alfredo Capucci

https://agent-manifest-spec.org

ORCID: 0009-0008-7216-3032
