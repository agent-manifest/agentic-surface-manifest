# Provider-Side Declarations for Automated Service Invocation: A Survey

Status: Research document. Non-normative.
Date: 2026-07-08
Author: Hernán Alfredo Capucci (ORCID 0009-0008-7216-3032)

## Abstract

This document surveys existing standards, protocol mechanisms, and standardization efforts relevant to provider-side declarations for services that may be invoked by automated reasoning systems at runtime. It evaluates fifteen declaration needs against ten bodies of prior art, records the coverage status of each need with citations to primary sources, and identifies the gaps that remain after coverage is accounted for. The document records evidence and analysis only; it does not propose or advocate a mechanism.

## 1. Methodology

The survey distinguishes two classes of declaration needs, which prior art treats differently:

- Content use: declarations by an asset holder regarding the use of digital assets (text, images, data) by automated systems, including AI training, search, and inference.
- Service invocation: declarations by a service operator regarding the invocation of the service's operations, where the decision to invoke is made by an automated reasoning system at runtime rather than ratified per call by a human.

Ten bodies of prior art were examined. Where a body is under active development, its source repository or draft text was read directly on 2026-07-08; the verified locations are recorded in the matrix and in the References section. Published standards are cited by document number. The following materials were verified against primary sources on the survey date:

1. IETF AI Preferences (AIPREF) Working Group: draft-ietf-aipref-vocab and draft-ietf-aipref-attach, full text from the working group repository [AIPREF-VOCAB] [AIPREF-ATTACH].
2. Model Context Protocol (MCP): the authoritative schema, schema/2025-06-18/schema.ts, 1,607 lines [MCP-SCHEMA].
3. Agent2Agent Protocol (A2A): specification/a2a.proto and docs/specification.md [A2A-PROTO] [A2A-SPEC].

The remaining bodies are cited from published, stable documents: the Robots Exclusion Protocol [RFC9309]; HTTP semantics [RFC9110]; security.txt [RFC9116]; OAuth 2.0 token revocation and authorization server metadata [RFC7009] [RFC8414]; JSON Web Signature [RFC7515]; the Open Digital Rights Language [ODRL]; the TDM Reservation Protocol [TDMREP]; Verifiable Credentials and Decentralized Identifiers [VC] [DID]; the Platform for Privacy Preferences [P3P], noting its obsoleted status; the OpenAPI Specification [OAS]; and two W3C Community Groups concerned with protocols and identity for autonomous software systems [W3C-AIAP] [W3C-AIR].

Coverage terminology. "Covered" indicates that at least one standardized or actively standardizing mechanism addresses the need in the channel where the relevant consumer reads. "Partially covered" indicates coverage limited to a subset of channels, subjects, or lifecycle stages. "Not covered" indicates that no standardized vocabulary or mechanism was found after examination of all ten bodies; such entries record the absence checks performed.

## 2. Coverage Matrix

| # | Declaration need | Status | Primary source | Observation |
|---|---|---|---|---|
| 1 | Content use by AI systems | Covered | [AIPREF-VOCAB] defines usage categories `train-ai` and `search` (consensus pending); [AIPREF-ATTACH] defines a `Content-Usage` HTTP header field and a `Content-Usage` directive for robots.txt; [TDMREP] provides a deployed reservation mechanism with a legal anchor in Article 4 of the EU DSM Directive | The content-use preference space is occupied by an active IETF standards-track effort and a deployed W3C CG mechanism. |
| 2 | Preference regarding automated invocation of services | Not covered | Absence verified in: [AIPREF-VOCAB], whose scope is "how digital assets are used by automated processing systems" (service invocation is not asset use); [RFC9309], which governs crawlers retrieving URIs rather than clients invoking operations; [MCP-SCHEMA] (no preference fields); [A2A-SPEC] (describes the agent, not the consumed resource); [ODRL] (expressible in the core model; no profile or vocabulary for agent invocation exists) | No standardized vocabulary exists for an operator to state, pre-interaction and in machine-readable form, a preference regarding invocation decided by automated systems. |
| 3 | Allowed / conditional / disallowed values for automated consumption | Not covered | Same absence checks as row 2. [AIPREF-VOCAB] defines an allow/disallow preference pattern per usage category, but its extension rule states that new categories "can be defined as a subset of an existing category, but not a superset" (Section "Vocabulary Extensions") | The value pattern exists in AIPREF; the scope does not. The subset-only extension rule formally precludes adding service invocation as an AIPREF category; the alternatives are a companion vocabulary reusing the AIPREF data model and attachment mechanisms, or recharter. |
| 4 | Usage terms by purpose | Partially covered | [ODRL] expresses purpose constraints, prohibitions, and duties (W3C Recommendation, 2018); [OAS] provides `info.termsOfService` as a URL to human-readable terms; terms of service exist as legal prose universally | Purpose constraints are expressible in ODRL today, but no ODRL profile defines autonomous software systems as a party class or invocation as an action class; no such vocabulary has been adopted in that ecosystem. |
| 5 | Retention of inputs submitted by automated clients | Not covered | Absence verified in [MCP-SCHEMA] (no fields matching contact, privacy, retention, or provider across 1,607 lines), [A2A-SPEC], [OAS], [AIPREF-VOCAB]. A directly analogous mechanism, machine-readable self-declared privacy practice, was standardized as [P3P] and obsoleted by W3C in 2018 following limited adoption and absent enforcement | The need is unaddressed by current mechanisms; the closest historical precedent was standardized and subsequently abandoned. Any future proposal in this cell must account for that precedent. A distinguishing hypothesis — that automated reasoning systems, unlike P3P-era user agents, natively consume machine-readable context — is a hypothesis, not evidence. |
| 6 | Use of submitted inputs for model training | Not covered (vocabulary) / partially covered (prose) | Vendor commitments of the form "API inputs are not used for training" are widespread as legal prose in terms of service; no standardized field carries them. [AIPREF-VOCAB] `train-ai` does not apply: it is declared by the asset holder about assets, whereas this need inverts the roles (the consumer requires a declaration from the provider) | Same status and same precedent considerations as row 5. |
| 7 | Accountable or responsible party | Partially covered | [A2A-PROTO]: message `AgentProvider` with fields `url` and `organization`, both REQUIRED; [OAS] `info.contact`; [VC] issuer identification. [MCP-SCHEMA]: no equivalent field (absence verified) | Covered for A2A agents and OpenAPI-described services; absent from MCP. The gap is a missing field in one protocol, not a missing vocabulary. |
| 8 | Operational and abuse contact | Covered | [RFC9116] (security.txt): mandatory `Contact` field at a well-known URI, published RFC; [OAS] `info.contact`; [A2A-PROTO] `AgentProvider.url` | RFC 9116 is security-oriented, but a standardized well-known contact declaration exists and is deployed. |
| 9 | Revocation or termination of access | Partially covered | [RFC7009] (OAuth 2.0 token revocation) together with [RFC8414] (authorization server metadata exposing `revocation_endpoint`, discoverable pre-interaction). No equivalent for API-key or MCP-native access (absence verified in [MCP-SCHEMA]) | Where OAuth is used, revocation is standardized and discoverable; elsewhere it exists only as prose. As with row 7, the residue is channel-level. |
| 10 | Rate limits and abuse terms | Partially covered | IETF HTTPAPI Working Group draft on RateLimit header fields [RATELIMIT]; widespread de facto `X-RateLimit-*` conventions; [RFC9116] for the abuse contact | In-channel, at-runtime declaration is largely solved de facto and is on a standardization path. No standardized pre-interaction declaration exists; its necessity is questionable, since a consumer learns the limits from the first response. |
| 11 | Per-operation safety hints | Covered | [MCP-SCHEMA] lines 871–922: `readOnlyHint`, `destructiveHint`, `idempotentHint`, `openWorldHint`, with explicit trust language: "all properties in ToolAnnotations are hints. They are not guaranteed to provide a faithful description of tool behavior... Clients should never make tool use decisions based on ToolAnnotations received from untrusted servers." OpenAI Actions define `x-openai-isConsequential` on OpenAPI operations | The dominant tool-invocation channel carries this layer, with the epistemic caveat written into the schema itself. |
| 12 | Mutation, destructiveness, idempotency | Covered | [RFC9110] defines safe and idempotent method semantics for HTTP; [MCP-SCHEMA] `destructiveHint` and `idempotentHint` | Covered both at the base protocol level (three decades of deployment) and in the tool-invocation channel. |
| 13 | Verification, identity, and signature of the declaring party | Covered (active body of work) | [A2A-SPEC] Sections on AgentCard signatures: JWS per [RFC7515], with a defined canonicalization procedure and a `signatures` field ([A2A-PROTO]); [VC]; [DID]; OpenID Connect claims; IETF WIMSE; [W3C-AIR]; the NIST NCCoE concept paper on agent identity and authorization | The question "can this declaration be trusted" has more active institutional coverage than any other row. Any declaration vocabulary should be designed to be carried within these envelopes rather than to compete with them. |
| 14 | Enforcement or proof of compliance | Not covered — and not addressable by declaration | No surveyed body attempts declarative enforcement. Enforcement is a runtime property (policy engines, sandboxing, validation frameworks) | This row is a category boundary rather than a gap. A declarative mechanism claiming enforcement would misrepresent its nature. |
| 15 | Multi-capability or multi-tool surface description | Covered | [MCP-SCHEMA] `tools/list`; [A2A-SPEC] `skills`; [OAS] `paths`; Agentic Resource Discovery catalogs (`ai-catalog.json`) | Capability enumeration is solved in each protocol channel and at the discovery layer. |

## 3. Remaining Gaps

After coverage is accounted for, four gaps remain. They differ in kind.

G1. Invocation preference (rows 2–3). No standardized, machine-readable, pre-interaction vocabulary exists for a service operator to express whether invocation of the service by automated reasoning systems is allowed, conditional, or disallowed. The absence was verified across all ten surveyed bodies. The most natural extension point, the AIPREF vocabulary, is formally precluded by its subset-only extension rule, which makes the gap structural rather than incidental. This is the only gap in the matrix without a partially covering mechanism or a failed precedent.

G2. Input-handling declaration (rows 5–6). No standardized field expresses the retention of, or training use of, inputs submitted by automated clients to a service. The gap is real but carries a documented precedent: P3P standardized machine-readable, self-declared data-handling practice and was obsoleted in 2018 after limited adoption. The historical record further shows that preference signals have succeeded when anchored in legal obligation (TDMRep following Article 4 of the EU DSM Directive; Global Privacy Control following the CCPA) and failed without such anchoring (P3P; Do Not Track). A proposal in this cell would need to state the distinguishing hypothesis explicitly and treat regulatory anchoring as a precondition signal.

G3. Accountable-party field in MCP (row 7). Present in A2A (`AgentProvider`, REQUIRED) and OpenAPI (`info.contact`); absent from the MCP schema. A field-level gap in one protocol.

G4. Revocation declaration outside OAuth (row 9). Standardized and discoverable where OAuth is deployed ([RFC7009], [RFC8414]); absent for API-key and MCP-native access. A field- or guidance-level gap in one protocol.

Rows 1, 8, 10, 11, 12, 13, and 15 are covered or partially covered to a degree that leaves no actionable residue. Row 14 is out of scope for any declarative mechanism by nature.

## 4. Recommended Contribution Paths

The paths below are recorded as venue-fit analysis. No path is advocated; the mapping follows from the structure of each gap.

G1 maps to two candidate venues. (a) An IETF path: a companion vocabulary reusing the AIPREF data model and the attachment mechanisms already defined in [AIPREF-ATTACH] (HTTP header field and robots.txt directive), proposed after the AIPREF v1 documents complete, since the subset-only rule precludes a direct extension and the working group's charter concerns content use. (b) A W3C path: a scope note to the AI Agent Protocol Community Group [W3C-AIAP], where agent-related vocabulary discussions are already in progress. Independent incubation is coherent only as a drafting stage for material intended for donation to one of these venues.

G2 maps to monitoring rather than construction. Candidate material can be prepared as annotation proposals for the protocol channel where consumers read (MCP), with any submission contingent on the appearance of an incentive anchor (for example, regulatory guidance on autonomous system deployments or explicit demand in protocol discussions). The P3P precedent indicates that construction in advance of incentive has the weakest historical record of any option in this survey.

G3 and G4 map to field-level proposals in the MCP specification process (implementation metadata carrying provider and contact information; revocation guidance for non-OAuth access). These are contributions to an existing specification, not new vocabulary.

Rows assessed as covered map to no action. Row 14 maps to no action under any circumstances, as declarative enforcement would misrepresent the mechanism.

## 5. Conclusions

1. The content-use declaration space (Q1) is institutionally occupied by an active IETF standards-track effort and a deployed W3C CG mechanism with legal anchoring. Work in this space would duplicate existing efforts.
2. Of fifteen surveyed declaration needs, eleven are covered, partially covered to the point of leaving no actionable residue, or outside the reach of declarative mechanisms by nature.
3. Two substantive gaps remain. The invocation preference (G1) is the only gap verified as structurally open: no mechanism addresses it, and the nearest extension point formally excludes it. The input-handling declaration (G2) is open but burdened by a directly analogous standardized mechanism that was obsoleted for lack of adoption; the historical evidence associates the success of preference signals with legal anchoring.
4. Two further gaps (G3, G4) are field-level absences in a single protocol and do not constitute vocabulary gaps.
5. The unresolved problem this survey set out to test therefore exists, but its verified extent is narrow: one open vocabulary gap, one precedent-burdened gap, and two protocol field gaps. Characterizations of the provider-side declaration space as broadly vacant are not supported by the evidence collected here.

This survey intentionally separates evidence from proposal. Whether the remaining gaps justify new standardization work remains an open question and should be evaluated within the relevant standards venues.

## 6. References

Primary sources verified in source form on 2026-07-08:

- [AIPREF-VOCAB] IETF AIPREF WG, "A Vocabulary For Expressing AI Usage Preferences", draft-ietf-aipref-vocab (adopted WG draft, standards track). Repository: github.com/ietf-wg-aipref/drafts. Sections cited: Vocabulary Definition (`train-ai`, `search`), Vocabulary Extensions (subset-only rule), Usage Category Labels.
- [AIPREF-ATTACH] IETF AIPREF WG, "Associating AI Usage Preferences with Content in HTTP", draft-ietf-aipref-attach (adopted WG draft, standards track). Defines the `Content-Usage` HTTP header field and the `Content-Usage` robots.txt directive.
- [MCP-SCHEMA] Model Context Protocol, authoritative schema, schema/2025-06-18/schema.ts (1,607 lines). Repository: github.com/modelcontextprotocol/modelcontextprotocol. Tool annotations at lines 871–922, including the quoted trust language. Absence checks performed for fields matching contact, privacy, retention, provider.
- [A2A-PROTO] Agent2Agent Protocol, specification/a2a.proto. Repository: github.com/a2aproject/A2A. `AgentProvider` (fields `url`, `organization`, REQUIRED); `signatures` field on AgentCard.
- [A2A-SPEC] Agent2Agent Protocol, docs/specification.md. AgentCard signing with JWS, canonicalization procedure, signature field exclusion rule.

Published standards and recommendations:

- [RFC7009] Lodderstedt, T., Ed., et al., "OAuth 2.0 Token Revocation", RFC 7009.
- [RFC7515] Jones, M., Bradley, J., Sakimura, N., "JSON Web Signature (JWS)", RFC 7515.
- [RFC8414] Jones, M., Sakimura, N., Bradley, J., "OAuth 2.0 Authorization Server Metadata", RFC 8414.
- [RFC9110] Fielding, R., Ed., Nottingham, M., Ed., Reschke, J., Ed., "HTTP Semantics", RFC 9110. Safe and idempotent method definitions.
- [RFC9116] Foudil, E., Shafranovich, Y., "A File Format to Aid in Security Vulnerability Disclosure", RFC 9116 (security.txt).
- [RFC9309] Koster, M., Illyes, G., Zeller, H., Sassman, L., "Robots Exclusion Protocol", RFC 9309.
- [ODRL] W3C, "ODRL Information Model 2.2", W3C Recommendation, 2018.
- [VC] W3C, "Verifiable Credentials Data Model", W3C Recommendation.
- [DID] W3C, "Decentralized Identifiers (DIDs) v1.0", W3C Recommendation.
- [P3P] W3C, "The Platform for Privacy Preferences 1.0 (P3P1.0) Specification". Obsoleted by W3C, 2018.
- [OAS] OpenAPI Initiative, "OpenAPI Specification". `info.contact`, `info.termsOfService`, `paths`; vendor extension `x-openai-isConsequential` defined by OpenAI Actions.

Bodies in progress, cited with status:

- [RATELIMIT] IETF HTTPAPI WG, "RateLimit header fields for HTTP" (Internet-Draft, work in progress).
- [TDMREP] W3C Text and Data Mining Reservation Protocol Community Group, "TDM Reservation Protocol (TDMRep)", CG Final Report; legal anchor in Directive (EU) 2019/790, Article 4.
- [W3C-AIAP] W3C AI Agent Protocol Community Group.
- [W3C-AIR] W3C Agent Identity Registry Protocol Community Group (proposed 2026-04-22).
- NIST NCCoE, "Accelerating the Adoption of Software and AI Agent Identity and Authorization", concept paper, February 2026.
