# Agentic Surface Manifest

Agentic Surface Manifest (ASM) is a declarative specification for digital surfaces that may be consumed by AI agents, agentic systems, or model-driven tools.

It complements Agent Manifest.

Agent Manifest declares actors.

Agentic Surface Manifest declares resources.

## Why this exists

Modern AI agents can invoke APIs, tools, MCP servers, web interfaces, and machine-readable services at runtime.

In many cases, the exposed service is not an agent. It does not pursue goals, initiate actions, or exercise autonomy. It is a surface consumed by agents.

Those surfaces still need a declaration layer.

They need to state:

- whether agentic consumption is allowed, restricted, or disallowed;
- what the surface exposes;
- how machine-readable descriptions are versioned and protected;
- what outputs may or may not contain;
- how inputs are handled;
- how access can be revoked;
- who is responsible.

## Actor-side and resource-side declaration

Agent Manifest addresses actor-side declaration.

Agentic Surface Manifest addresses resource-side declaration.

Together, they form a two-sided declaration layer for agentic interaction.

## Core idea

A surface becomes agentic when decisions to invoke or interpret it are made by an automatic reasoning system at runtime, using machine-readable descriptions as operational input.

The key question is not whether a service uses AI internally.

The key question is who decides to invoke it.

## Status

Early draft.

This repository is exploratory and pre-standardization.

No production conformance claims should be made yet.

## License

Code, schemas, and tooling are licensed under Apache-2.0.

Specification text and documentation are intended to be made available under CC BY 4.0 unless otherwise noted.
