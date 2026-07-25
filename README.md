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

## Links

- [Website](https://instanda.com/)
- [Platform Overview](https://instanda.com/platform-overview)
- [Cloud / integration model](https://instanda.com/cloud)
- [Partners and integration ecosystem](https://instanda.com/partners)
- [Support portal (login required)](https://support.instanda.com/)
- [Trust Centre](https://app.trustero.com/trust/instanda)
- [Platform Security](https://instanda.com/platform-security)
- [Blog](https://instanda.com/blog)
- [News](https://instanda.com/news)
- [LinkedIn](https://uk.linkedin.com/company/instanda)

## Review

See [review.yml](review.yml) for the full API Evangelist review, probe-by-probe HTTP statuses, ACORD assessment, and the quote/bind/issue/FNOL exposure breakdown.
