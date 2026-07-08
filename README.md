# Agentic Surface Manifest

Status: research incubation.

This repository investigates whether exposed digital surfaces consumed by AI agents require a standalone manifest, an extension to existing protocols, or a vocabulary profile for existing standards.

No production specification is currently proposed.

## Research question

Modern AI agents can invoke APIs, tools, MCP servers, web interfaces, and machine-readable services at runtime.

In many cases, the exposed service is not itself an agent. It may be a resource, endpoint, tool, API, or surface consumed by agents.

The question of this repository is:

> What, if anything, should such exposed surfaces declare before they are consumed by agentic systems?

## Current direction

This work is exploratory.

It will compare possible approaches, including:

- extensions to existing AI preference vocabularies;
- MCP tool annotations;
- ODRL profiles;
- machine-readable terms of use;
- and, only if necessary, a standalone Agentic Surface Manifest.

## Relationship to Agent Manifest

Agent Manifest declares actors.

This repository studies whether a separate resource-side declaration is needed for exposed surfaces.

No changes to Agent Manifest v1.0 are implied by this repository.

## Non-goals

This repository does not define:

- agent execution;
- communication protocols;
- discovery mechanisms;
- authorization systems;
- verification or attestation;
- enforcement;
- scoring;
- transport.

It investigates declaration only.

## Status

Early research incubation.

Everything may change.

Do not make production conformance claims based on this repository.

## License

Code, schemas, examples, and tooling are licensed under Apache-2.0.

Specification prose and documentation are intended to be licensed under CC BY 4.0 unless otherwise noted.
