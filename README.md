# INSTANDA (instanda)

INSTANDA is a London-headquartered no-code insurance core-systems vendor, trading as F2X Group Limited (England and Wales no. 05236974) from 70 Gracechurch Street in the City of London, a few streets from Lloyd's. Founded in 2015 by Tim Hardcastle (CEO) and Derek Hill (Group CRO), it sells a cloud-native policy administration and digital distribution platform to insurance carriers, MGAs and brokers, letting business users configure products, rating, rules, documents, agent/broker portals and direct-to-consumer journeys without writing code. Its footprint spans property and casualty, life and health, and specialty lines across the UK, EMEA, North America and APAC, and it is architected on Microsoft Azure.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/instanda/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/instanda/refs/heads/main/apis.yml)

## Tags

- Insurance
- United Kingdom
- Insurtech
- Policy Administration
- Underwriting
- Claims
- Property and Casualty
- Life Insurance
- Health Insurance
- Digital Distribution
- No Code
- Core Systems
- MGA
- Broker
- Webhooks
- Microsoft Azure
- Embedded Insurance

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

None listed. This is an honest stub.

INSTANDA markets itself as "API-first, cloud-native", and at the product level that is real: the platform generates per-product REST and SOAP interfaces described with Swagger or WSDL definitions, supports API call-out steps inside rating, and fires webhooks for real-time customer event notifications. None of it is public.

- No developer portal. `developer.instanda.com`, `developers.instanda.com`, `docs.instanda.com`, `api-docs.instanda.com`, `/developers`, `/api`, `/developer` and `/integrations` all return **404**.
- `api.instanda.com` is a live host but answers anonymous `GET /` with **403 Forbidden** — no body, no `WWW-Authenticate` challenge, no reference documentation. Every spec path probed beneath it (`/swagger/v1/swagger.json`, `/openapi.json`, `/api-docs`, `/docs`, `/help`) returns 404.
- The only documentation surface, `support.instanda.com`, is a **Freshdesk login wall** (302 to Freshworks OAuth) for licensed customers.
- **0 OpenAPI/Swagger documents** could be harvested, so there is no `openapi/` directory in this repo.
- No public GraphQL, no published `.proto`, no AsyncAPI, and no first-party Postman workspace. The GitHub account [github.com/instanda](https://github.com/instanda) exists but has no public repositories.
- **ACORD posture:** no ACORD reference found. No mention of ACORD, AL3, ACORD XML, NGDS, IVANS, Applied Epic or Vertafore AMS360 anywhere on the public site. The nearest agency/broker seam is an Applied Systems (Applied TAM) broker management system integration listed in the partner directory.

Quote, bind, issue and FNOL all exist as platform capabilities — policyholders can quote and bind, make policy changes, pay bills and submit a First Notice of Loss, and embedded distribution can be "embedded on websites via API" — but every one of those verbs is reachable only through a licensed tenant or a partner integration. That is the finding: a core system whose API is real, and invisible.

## Enrichment round — 2026-07-25

The answer above did not change, but three public surfaces the first pass missed were found and captured.

**1. The Swagger UI exists, and it is gated.** `instanda.com/robots.txt` carries a single revealing line — `Disallow: https://design.instanda.com/` — which exposes the tenant product-configuration application (ASP.NET on Azure). On that host, `https://design.instanda.com/swagger/index.html` is a **registered route**: a `HEAD` returns, repeatably, `302 → /Account/LogOn?ReturnUrl=%2fswagger%2findex.html`, while an unknown path such as `/zzzfake` hard-404s and `/swagger`, `/swagger/`, `/swagger/ui/index` and `/swagger/v1/swagger.json` all 404. Swagger UI is on the platform, behind forms authentication, serving nothing anonymously. The finding upgrades from "no Swagger anywhere" to "Swagger UI confirmed at a known URL, authentication-gated" — and `openapi/` still stays empty.

**2. A public, component-level status page.** [status.instanda.com](https://status.instanda.com/) (SorryApp) is not linked from the site footer and there is no `/status` path on the apex; it was found by DNS sweep. It is fully public and it is the richest public description of the platform's real functional surface — four hosting regions (AU, EMEA, JP, NA), each publishing Design, Production sites and ODS, plus monitored **Quote Engine, Referrals, Renewals, MTAs, Endorsements, Multi Items, Claims, Reports**, three email classes, Online Payments, and **Event Webhooks**. No incident-history feed is published; subscription is by email and Slack.

**3. The best public statement of the webhook contract.** The Event Webhooks component on that status page reads, verbatim: *"Event Webhooks allow Instanda to send information to another system. When an event happens, such as an update to a policy, Instanda will HTTP POST the information to a URL of your choice."* Transport, verb, subscriber-supplied endpoint and one named example event — more than the marketing site says. Still no catalog, no payload schemas, no signing scheme, no retry policy.

Also confirmed: a named certification set on the first-party security page — **ISO 27001:2022, SOC 2, Cyber Essentials, PCI DSS SAQ A** — and a clean negative sweep for client libraries (npm, PyPI, NuGet, RubyGems, Packagist, crates.io all empty), MCP servers, changelogs, roadmaps, pricing and `security.txt`.

`apis[]` stays empty. Listing an API whose contract is generated per tenant and never published would still be fabrication.

## Artifacts

- [lifecycle/instanda-lifecycle.yml](lifecycle/instanda-lifecycle.yml) — status page, regions, monitored components, versioning and SLA posture
- [asyncapi/instanda-webhooks.yml](asyncapi/instanda-webhooks.yml) — the Event Webhooks surface as published
- [conformance/instanda-conformance.yml](conformance/instanda-conformance.yml) — standards and certifications, each with its evidence
- [security/instanda-domain-security.yml](security/instanda-domain-security.yml) — TLS, HSTS, DNSSEC, CAA, SPF, DMARC probe
- [security/instanda-trust-center.yml](security/instanda-trust-center.yml) — trust centre and published security controls
- [well-known/instanda-well-known.yml](well-known/instanda-well-known.yml) — the negative `/.well-known/` probe record across all three hosts
- [llms/instanda-llms.txt](llms/instanda-llms.txt) — agent-readable summary of what is and is not available

## Links

- [Website](https://instanda.com/)
- [Platform Overview](https://instanda.com/platform-overview)
- [Cloud / integration model](https://instanda.com/cloud)
- [Status page](https://status.instanda.com/)
- [Partners and integration ecosystem](https://instanda.com/partners)
- [Support portal (login required)](https://support.instanda.com/)
- [Platform log-on (tenant application)](https://design.instanda.com/Account/LogOn)
- [Trust Centre](https://app.trustero.com/trust/instanda)
- [Platform Security](https://instanda.com/platform-security)
- [Blog](https://instanda.com/blog)
- [News](https://instanda.com/news)
- [GitHub](https://github.com/instanda)
- [LinkedIn](https://uk.linkedin.com/company/instanda)

## Review

See [review.yml](review.yml) for the full API Evangelist review, 35 probe-by-probe HTTP statuses, ACORD assessment, and the quote/bind/issue/FNOL exposure breakdown.
