# Canada Life (canada-life)

The Canada Life Assurance Company is one of Canada's largest life and health insurers, formed from the 2020 amalgamation of Great-West Life, London Life and Canada Life under Winnipeg-based parent Great-West Lifeco. From its home market of Canada it underwrites individual life insurance, critical illness and disability coverage, individual and group health and dental benefits, group retirement and savings, segregated funds and annuities, distributed through an advisor and managing-general-agent channel rather than direct-to-developer.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/canada-life/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/canada-life/refs/heads/main/apis.yml)

## API posture

Canada Life publishes **no public, self-serve developer portal and no downloadable API specifications**. This repository records that honestly rather than inventing a surface to fill the record.

- **Developer portal:** none. `developers.canadalife.com` survives only as a dangling DNS CNAME to `prod-canadalife-portal.apigee.net`, which no longer resolves (NXDOMAIN) — a retired Apigee developer portal whose record was never cleaned up. `developer.canadalife.com` and `docs.canadalife.com` do not resolve at all, and `/developers`, `/api`, `/developer`, `/partners` and `/integrations` on the main site all return 404.
- **Gateway:** `api.canadalife.com` is live and returns **403 Forbidden on every path probed**, including `/openapi.json`, `/swagger.json`, `/api-docs`, `/v1/openapi.json` and `/graphql`.
- **Auth:** OAuth2 client credentials only. The OpenID discovery document and JWKS are the only anonymously readable endpoints (both HTTP 200). The authorization endpoint is published literally as `/oauth2/v1/authorize-NOT-SUPPORTED`, so the interactive authorization-code flow is switched off by design. `scopes_supported` is an empty array.
- **Partner surfaces:** `advisor.canadalife.com` redirects to a Liferay "Digital Agent" advisor login wall; `my.canadalife.com` is a Salesforce-hosted retail customer portal. Both are login walls, neither is a developer portal.
- **ACORD posture:** no first-party ACORD reference anywhere on canadalife.com (0 matches across 1,236 URLs in the public English sitemap). The real posture is indirect — Canada Life is a listed **carrier member of CLIEDIS**, the Canadian Life Insurance EDI Standards body, which distributes **ACORD XML for Life v2.48** through its CAIR tool and defines the e-application, pending-policy and Book-of-Business feeds carriers exchange with distributors.
- **Quote / bind / issue / FNOL:** none exposed publicly. All four run advisor-side, through the Digital Agent portal or the CLIEDIS ACORD feed set.
- **Webhooks / AsyncAPI / Postman / GraphQL / gRPC:** none published. The absence of an event catalog is itself the finding.

Canada operates under the most fragmented insurance supervision of the major markets — OSFI supervises federally-regulated insurers prudentially while the provinces (FSRA in Ontario, AMF in Quebec) regulate market conduct — with **no open-insurance mandate**, and Consumer-Driven Banking excludes insurance entirely. There is no forcing function, and Canada Life's posture reflects that exactly.

## Tags

- Insurance
- Canada
- Life Insurance
- Health Insurance
- Employee Benefits
- Group Retirement
- Carrier
- ACORD
- Partner Gated
- No Public API

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

None. `apis[]` is intentionally empty — Canada Life documents no public API.

## Links

- [Website](https://www.canadalife.com/)
- [About Us](https://www.canadalife.com/about-us.html)
- [Sign In](https://www.canadalife.com/sign-in.html)
- [Advisor Portal (login wall)](https://advisor.canadalife.com/login)
- [Customer Portal (login wall)](https://my.canadalife.com/)
- [CLIEDIS members list (ACORD evidence)](https://www.cliedis.ca/who-we-are/members)
- [LinkedIn](https://www.linkedin.com/company/canada-life)

## Review

See [review.yml](review.yml) for the full probe log, HTTP statuses, harvested OpenID discovery document, and ACORD provenance.
