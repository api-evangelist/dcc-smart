# Smart DCC

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Smart DCC (the Data Communications Company) is the Ofgem-licensed monopoly that operates Britain's national smart metering communications network, connecting electricity and gas smart meters in homes and businesses to energy suppliers, network operators and other authorised users over a single secure wide-area network. It sits in the middle of the United Kingdom energy value chain as shared infrastructure rather than as a retailer or a data marketplace, and it is regulated through the Smart Meter Communication Licence and governed by the Smart Energy Code. Its API posture reflects that position exactly. Britain mandated the infrastructure, not a consumer data right — there is no UK equivalent of the Australian Consumer Data Right for energy, so Smart DCC operates no consumer data-portability API and publishes no Green Button or Consumer Data Standards surface. The real production interface is the DCC User Interface Specification (DUIS), an XML web service reached over a DCC User Gateway Connection, plus the Self-Service Interface; the DUIS specification and its XML schema are published openly as Smart Energy Code subsidiary documents, but the gateway itself is closed to anyone who has not acceded to the Smart Energy Code and passed SMKI and User Entry Process Testing. The only self-serve, machine-readable contract Smart DCC publishes is an OpenAPI for the open-source DCC Boxed DUIS signing and validation tool on GitHub. Network statistics are shown on a public dashboard as a rendered web page with no documented open data API or bulk download, so both the consumer-data and market-data sides are effectively closed while the interface specification itself is open.

**Areas:** Energy · United Kingdom · Utilities · Electricity · Gas · Smart Metering · Grid · Metering Infrastructure · Energy Data

## Smart DCC on APIs.io

Everything profiled for Smart DCC is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/dcc-smart/](https://apis.io/providers/dcc-smart/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [Smart DCC Sign API](https://apis.io/apis/dcc-smart/dcc-smart-sign-api/) — The Sign API from Smart DCC — 1 operation(s) for sign.
- [Smart DCC Verify API](https://apis.io/apis/dcc-smart/dcc-smart-verify-api/) — The Verify API from Smart DCC — 1 operation(s) for verify.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [dcc-smart-mcp.yml](https://apis.io/servers/dcc-smart/dcc-smart-mcp-yml/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Dcc Smart Agentic Access](https://apis.io/agentic-access/dcc-smart/dcc-smart-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Dcc Smart Dccboxed Keystore](https://apis.io/schemas/dcc-smart/dcc-smart-dccboxed-keystore/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [Dcc Smart Vocabulary](https://apis.io/vocabularies/dcc-smart/dcc-smart-vocabulary/)

#### Collections (1)

Postman and Open Collection request collections.

- [DCC Boxed DUIS Signing Tool API](https://apis.io/collections/dcc-smart/open-dcc-boxed-duis-signing-tool/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Dcc Smart Dcc Boxed Duis Signing Tool Overlay](https://apis.io/overlays/dcc-smart/dcc-smart-dcc-boxed-duis-signing-tool-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Dcc Smart Authentication](https://apis.io/security/dcc-smart/dcc-smart-authentication/)
- [Dcc Smart Domain Security](https://apis.io/security/dcc-smart/dcc-smart-domain-security/)
- [Dcc Smart Vulnerability Disclosure](https://apis.io/security/dcc-smart/dcc-smart-vulnerability-disclosure/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.smartdcc.co.uk/)
- [Documentation](https://www.smartdcc.co.uk/document-centre/)
- [Pricing](https://www.smartdcc.co.uk/about-dcc/governance-regulations/charges/)
- [Support](https://www.smartdcc.co.uk/contact-us-service-users/)
- [Changelog](https://github.com/SmartDCCInnovation/dccboxed-signing-tool/releases)
- [Blog](https://www.smartdcc.co.uk/news-events/)
- [Security](https://www.smartdcc.co.uk/media/sn5dn4hr/information-security-policy-3.pdf)
- [Compliance](https://www.smartdcc.co.uk/about-dcc/governance-regulations/governance-reports-policies/)
- [Privacy policy](https://www.smartdcc.co.uk/privacy-notice/)
- [GitHub](https://github.com/SmartDCCInnovation)
- [Status](https://www.smartdcc.co.uk/our-smart-network/network-data-dashboard/performance/)

## API Evangelist rating

**Kin Score 44.8** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 64.3 |
| Contract quality | 43.5 |
| Contract governance | 22.0 |
| Operational transparency | 50.0 |
| Developer ergonomics | 51.8 |
| Access clarity | 28.9 |

**Agent readiness 29.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | na |

**Regulatory alignment 32.8** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/dcc-smart/](https://apis.io/providers/dcc-smart/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Smart DCC: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/dcc-smart/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
