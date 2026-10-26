# Particle (particle)

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

Particle is an integrated IoT Platform-as-a-Service that provides cellular, Wi-Fi, and Bluetooth hardware modules alongside a comprehensive cloud platform for building and managing connected devices at scale. The Particle Device Cloud exposes a REST API enabling developers to call device functions, read variables, publish and subscribe to events, manage firmware OTA updates, and administer product fleets. Authentication uses OAuth 2.0 bearer tokens, and the platform supports JavaScript, iOS, Android, and Windows SDKs as well as a command-line interface. Particle's pricing model is based on Data Operations consumed per month, with plans ranging from a free prototyping tier through paid block-based plans to enterprise contracts.

APIs.json: [https://raw.githubusercontent.com/api-evangelist/particle/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/particle/refs/heads/main/apis.yml)

Naftiko: [https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=particle-api-evangelist&utm_content=repo](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=particle-api-evangelist&utm_content=repo)

## Tags

IoT, Internet of Things, Cellular, Wi-Fi, Bluetooth, Device Management, Firmware, OTA Updates, Fleet Management, Hardware, Embedded

## APIs

### Particle Cloud API

The Particle Cloud REST API enables developers to interact with Particle-connected devices — calling device functions, reading variables, publishing and subscribing to events, managing SIM cards, performing OTA firmware updates, and administering product fleets. All requests use OAuth 2.0 bearer tokens and target https://api.particle.io.

- **Documentation:** https://docs.particle.io/reference/cloud-apis/api/
- **Getting Started:** https://docs.particle.io/getting-started/cloud/cloud-api/
- **Base URL:** https://api.particle.io

## Plans / Rate Limits / FinOps

| Resource | Path |
|---|---|
| Plans & Pricing | [plans/particle-plans-pricing.yml](plans/particle-plans-pricing.yml) |
| Rate Limits | [rate-limits/particle-rate-limits.yml](rate-limits/particle-rate-limits.yml) |
| FinOps | [finops/particle-finops.yml](finops/particle-finops.yml) |

**Pricing summary:** Free tier (100 devices, 100K Data Operations/month). Basic $299/block/month (100 devices, 720K Data Ops). Plus $599/block/month (100 devices, 5M Data Ops). Professional and Enterprise available at custom pricing.

**Rate limits:** General API: 10,000 req/5 min per IP. Token creation: 100 req/5 min per IP (30-min lockout after 10 failures). Events retrieval: 100 req/5 min per IP. Device serial lookup: 50 req/hr per user. Concurrent SSE streams: 100 per IP. HTTP 429 on throttle.

## Timestamps

- **Created:** 2026-06-12
- **Modified:** 2026-06-12

## Common Properties

| Type | URL |
|---|---|
| Website | https://www.particle.io/ |
| Documentation | https://docs.particle.io/ |
| Developer Portal | https://www.particle.io/developer-tools/ |
| GitHub Organization | https://github.com/particle-iot |
| Blog | https://www.particle.io/blog/ |
| Changelog | https://changelog.particle.io/ |
| Status Page | https://status.particle.io/ |
| Pricing | https://www.particle.io/pricing/ |
| LinkedIn | https://www.linkedin.com/company/wwwparticleio |
| X (Twitter) | https://x.com/particle |
| Community | https://community.particle.io/ |

## Maintainers

- **Kin Lane** — kin@apievangelist.com
