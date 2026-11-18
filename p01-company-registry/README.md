# Taiwan Company Registry — Clean English JSON (September 2026)

Every company newly registered in Taiwan in September 2026 — cleaned,
structured, and translated into English.

**2,915 companies. One file. No Chinese required.**

## What this repo is

A free sample of a paid dataset. This repo contains:

- **`free-sample-100.json`** — 100 real records from the September 2026
  file, in the exact schema of the full dataset. Download it, inspect it,
  build against it. If the format works for you, the full month is the
  same thing, 2,915 records instead of 100.
- **`business-item-glossary.json`** — the hand-built English glossary for
  Taiwan's standard business-item descriptions: 338 entries, Chinese
  description → English translation. This is the glossary used to
  translate the business scopes in the sample. The glossary in the paid
  package covers all 796 codes (see below).

The full dataset is **not** in this repo. It is available as a one-time
purchase — see [Get the full dataset](#get-the-full-dataset).

## What's inside each record

| Field | Description |
|---|---|
| `unified_business_number` | 統一編號 (UBN), 8 digits, unique |
| `company_name_zh` | Company name as filed |
| `company_name_en` | Always `null` — the register publishes no official English names, and none are invented here |
| `status_en` | Approved for establishment / Approved for registration / Dissolved |
| `capital_twd` | Registered capital in TWD (integer) |
| `incorporation_date` | ISO 8601 date (ROC date + 1911) |
| `address_en` | Structured English address: county/city, district, village, road, section, lane, alley, house number, floor, room — plus a formatted postal-style string. Transliterated to Hanyu Pinyin with standard English place names |
| `business_items` | Registered business scope: each standard item code with its Chinese description and an English translation |
| `source` | Source datasets, licence, and attribution (identical in every record) |

## Who it's for

- **Developers** building company-enrichment, KYB, or lead-generation
  products that cover Taiwan.
- **Researchers and analysts** who need Taiwan's new-company flow in
  English without reading Chinese.

## Coverage (full dataset)

- **Month:** September 2026 — dataset 6047, Company Registration
  Checklist (Monthly), Administration of Commerce, Ministry of Economic
  Affairs (Taiwan). Incorporation dates run 2026-08-27 to 2026-09-30
  (the "September" file includes filings approved in the last days of
  August).
- **Records:** 2,915, across 21 counties/cities. Taipei City 693,
  Taichung City 516, New Taipei City 502, Kaohsiung City 326, Taoyuan
  City 296, Tainan City 173, and 15 more.
- **Registered capital:** NT$0 – NT$3,909,811,100, median NT$1,000,000.
- **Business items:** 50,039 in total, 17.2 per company on average, 600
  distinct standard codes — translated with a hand-built glossary of 796
  entries covering 100% of the descriptions in the file.
- **Format:** JSON (nested, same schema as the sample) + flat CSV
  (30 columns, UTF-8 with BOM).

## Get the full dataset

**US$29 one-time** for the full September 2026
file — JSON + CSV, 2,915 records.

- [Buy the full dataset — US$29 one-time](https://forestcraft.gumroad.com/l/fsliec) *(Gumroad purchase page, live since 2026-11-10)*
- Sample download: `free-sample-100.json` in this repo.

## What buyers do NOT get

Be clear about this before you buy:

- **No official English company names.** The GCIS register does not
  publish them and does not require companies to have one.
  `company_name_en` is always `null`; no name was ever invented.
- **No contact information.** No phone numbers, email addresses, or
  websites — none exist in the source data.
- **No representative (director) names.** Excluded by default under
  Taiwan's Personal Data Protection Act.
- **No real-time data and no prices.** A one-month snapshot (September
  2026). Statuses are as of 2026-11-06; 2 companies were already
  dissolved by then.
- **No verified business scope for 26 companies (0.9%).** The GCIS
  open-data APIs return no record for them at all. Their status and
  business items are `null` with an explanatory note. This is unknown
  data, not empty data.

## Sources

- **Monthly checklist (source of truth):** 公司設立登記清冊(月份),
  dataset 6047, Administration of Commerce, Ministry of Economic
  Affairs (Taiwan) — https://data.gov.tw/dataset/6047 — September 2026
  file (CSV, 2,915 records, retrieved 2026-11-06).
- **Enrichment:** 公司登記基本資料-應用三 (Basic Company Registration
  Information — Application Three), dataset 22198, same agency —
  https://data.gov.tw/dataset/22198 — one API lookup per company.
- **Business-item code table:** 公司行號營業項目代碼表, dataset 8295
  (788 codes; the full glossary covers all of them plus 4 codes the
  table omits and 3 post-table renames).

## Licence — OGDL-Taiwan-1.0

All source data is released under the **Open Government Data License,
Taiwan 1.0 (OGDL-Taiwan-1.0)** — https://data.gov.tw/license.

The licence requires attribution. The attribution text is embedded in
every record's `source` block:

> Administration of Commerce, Ministry of Economic Affairs (Taiwan),
> 2026, Company Registration Checklist (Monthly),
> https://data.gov.tw/license

If you republish or resell this data, keep that attribution. Failure to
attribute voids the licence.

## Method (summary)

Dates: ROC + 1911 → ISO 8601. Addresses: parsed and transliterated
(2,915/2,915 parsed, 0 failures) — Hanyu Pinyin, standard English
county/city names, North/South/East/West/Central districts, road
suffixes Rd./St./Blvd., directional suffixes S./N./E./W. Business
items: enriched per company from GCIS Application Three (dataset 22198)
and translated with the 796-entry hand-built glossary. Representative
names excluded. OGDL attribution embedded in every record.

**Known quirk (documented):** 51 records carry a first-suffix district
mis-split inherited from the validation sample's parsing rule — 前鎮區 →
`Qian Town` (33), 平鎮區 → `Ping Town` (15), 新市區 → `Xin City` (3),
with a leading 區 leaking into the road name. This is a parsing
artefact, not a data error in the register; it is kept identical to the
sample for consistency. The full package's VALIDATION.md documents it in
full.

## Update frequency

This file is a **single-month snapshot** (September 2026). It is not
updated. A new month is a new file. The underlying monthly checklist
(dataset 6047) is published monthly by the Administration of Commerce.
