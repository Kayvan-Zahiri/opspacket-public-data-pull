# Sample schema — Open Brewery DB (California slice)

**Purpose:** Public portfolio sample for OpsPacket Public Data Pull (EXP-003). Not a client deliverable.

## Source
- **API:** https://api.openbrewerydb.org/v1/breweries (Open Brewery DB — public, no API key)
- **Query:** `per_page=40&by_state=california`
- **Pulled:** 2026-09-28 (PT)
- **License / ToS posture:** Open Brewery DB is a free public API intended for this kind of use. Sample omits phone numbers intentionally (demo hygiene vs spam-list optics). Business names/addresses/websites are public directory fields.

## Hard-rule compliance
- Public JSON endpoint only — no login, no CAPTCHA bypass, no robots.txt violation
- No personal email harvest
- Ephemeral demo; data may go stale as the upstream API updates

## Output file
`openbrewerydb-california-sample.csv` — **40** rows, **10** fields, deduped by `id`

## Fields

| Field | Type | Nulls (n/40) | Notes |
| --- | --- | ---: | --- |
| id | string (UUID) | 0 | Upstream brewery id |
| name | string | 0 | Display name |
| brewery_type | string | 0 | e.g. micro, brewpub, large, closed |
| city | string | 0 | |
| state | string | 0 | Full state name from API |
| postal_code | string | 0 | |
| country | string | 0 | |
| website_url | string | 4 | Empty when upstream null |
| longitude | number/string | 0 | WGS84 |
| latitude | number/string | 0 | WGS84 |

## Row counts / quality
- Requested cap: 40 · Returned: 40 · Deduped: 40
- Null rate highest on `website_url` (10%)
- No guaranteed freshness after pull date

## What a paid Data Pull adds
Your URL pattern + field list → same shape (CSV + this style of schema.md + null rates), scoped ≤5,000 rows / ≤12 fields, ≤72h standard or ≤24h rush.
