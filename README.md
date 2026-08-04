# Smart DCC (dcc-smart)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Smart DCC (the Data Communications Company) is the Ofgem-licensed monopoly that operates Britain's national smart metering communications network, connecting electricity and gas smart meters in homes and businesses to energy suppliers, network operators and other authorised users over a single secure wide-area network. It sits in the middle of the United Kingdom energy value chain as shared infrastructure rather than as a retailer or a data marketplace, and it is regulated through the Smart Meter Communication Licence and governed by the Smart Energy Code. Its API posture reflects that position exactly. Britain mandated the infrastructure, not a consumer data right — there is no UK equivalent of the Australian Consumer Data Right for energy, so Smart DCC operates no consumer data-portability API and publishes no Green Button or Consumer Data Standards surface. The real production interface is the DCC User Interface Specification (DUIS), an XML web service reached over a DCC User Gateway Connection, plus the Self-Service Interface; the DUIS specification and its XML schema are published openly as Smart Energy Code subsidiary documents, but the gateway itself is closed to anyone who has not acceded to the Smart Energy Code and passed SMKI and User Entry Process Testing. The only self-serve, machine-readable contract Smart DCC publishes is an OpenAPI for the open-source DCC Boxed DUIS signing and validation tool on GitHub. Network statistics are shown on a public dashboard as a rendered web page with no documented open data API or bulk download, so both the consumer-data and market-data sides are effectively closed while the interface specification itself is open.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dcc-smart/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dcc-smart/refs/heads/main/apis.yml)

## Tags

- Energy
- United Kingdom
- Utilities
- Electricity
- Gas
- Smart Metering
- Grid
- Metering Infrastructure
- Energy Data

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### DCC Boxed DUIS Signing Tool API

An open-source HTTP API published by Smart DCC Limited for signing and validating DUIS (DCC User Interface Specification) XML messages. Two operations — `POST /sign` adds an XML digital signature to a Base64-encoded unsigned DUIS request (with an optional `preserveCounter` flag), and `POST /verify` validates the signature on a DUIS response and strips it. The tool ships with the ZAZ1 test SMKI certificates used by DCC Boxed and also performs XSD validation. It runs locally as a self-hosted server; Smart DCC operates no public hosted instance.

- **Human URL:** [https://github.com/SmartDCCInnovation/dccboxed-signing-tool](https://github.com/SmartDCCInnovation/dccboxed-signing-tool)
- **Base URL:** `http://localhost:8080`

#### Tags

- Smart Metering
- DUIS
- Signing
- Validation
- Testing

#### Properties

- [OpenAPI](openapi/dcc-boxed-duis-signing-tool-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://github.com/SmartDCCInnovation/dccboxed-signing-tool)
- [Source Code](https://github.com/SmartDCCInnovation/dccboxed-signing-tool)
- [Specification](https://smartenergycodecompany.co.uk/documents/sec-subsidiary-documents/sec-appendix-ad-dcc-user-interface-specification-duis/)

## Common Properties

- [Website](https://www.smartdcc.co.uk/)
- [About](https://www.smartdcc.co.uk/about-dcc/)
- [Contact](https://www.smartdcc.co.uk/contact-us/)
- [Blog](https://www.smartdcc.co.uk/news-events/)
- [GitHub Organization](https://github.com/SmartDCCInnovation)
- [Documentation](https://www.smartdcc.co.uk/document-centre/)
- [Onboarding](https://www.smartdcc.co.uk/partner-with-the-dcc/)
- [Specification — DUIS v5.3 (PDF)](https://www.smartdcc.co.uk/media/d5kh4khf/dcc-user-interface-specification-v53-18-mar-2025.pdf)
- [Specification — SEC Appendix AD (DUIS)](https://smartenergycodecompany.co.uk/documents/sec-subsidiary-documents/sec-appendix-ad-dcc-user-interface-specification-duis/)
- [Specification — SEC Appendix AE (DCC User Interface Code of Connection)](https://smartenergycodecompany.co.uk/documents/sec-subsidiary-documents/sec-appendix-ae-dcc-user-interface-code-of-connection/)
- [Schema — DUIS XML Schema V5.1](https://www.smartdcc.co.uk/media/6490/duis-xml-schema-v51.docx)
- [Dashboard](https://www.smartdcc.co.uk/our-smart-network/network-data-dashboard/)
- [Products — DCC Boxed](https://www.smartdcc.co.uk/our-smart-network/network-products-services/dcc-boxed/)
- [Regulation — Smart Energy Code](https://smartenergycodecompany.co.uk/the-smart-energy-code/)

## Mandate and Access Posture

- **Mandate regime:** `smart-meter-infrastructure` — the Smart Meter Communication Licence and the Smart Energy Code compel the *network*, not consumer data portability.
- **Mandate status:** `live-implemented` for the infrastructure mandate only. Verified by fetching the DUIS v5.3 specification (HTTP 200), the DUIS XML Schema V5.1 (HTTP 200), and SEC Appendices AD and AE (HTTP 200), plus the live public network dashboard.
- **Consumer data right:** none. No UK CDR-energy equivalent, no Green Button regulation, no accredited-recipient register.
- **Data standard:** DUIS v5.3 / GBCS / SMETS2 / SMKI — UK-specific, code-governed XML. No Green Button, CDR Consumer Data Standards, OCPP, OCPI, OpenADR, IEEE 2030.5, or IEC CIM reference found.
- **Consumer data API:** no. **Open market data API:** no — the network dashboard is a rendered page with no feed or download.
- **Access gate:** `application-approval`. Accede to the Smart Energy Code, order a DCC User Gateway Connection, build or buy a DUIS implementation, obtain SMKI certificates, then pass SREPT and UEPT.
- **Auth model:** SMKI PKI with XML digital signatures over a governed Code of Connection. No API keys, no OAuth 2.0, no OpenID Connect (`/.well-known/openid-configuration` returned HTTP 404).

## Review

See [review.yml](review.yml) for every URL probed, the HTTP status of each, and the full mandate / consumer-versus-market-data analysis.
