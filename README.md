# Particle (particle)

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
