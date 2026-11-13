# AI Sec Watch Dataset: AI/LLM Security Threat Intelligence

Version 4.0, generated on 2026-10-10. Concept DOI 10.5281/zenodo.19519469 always resolves to the latest version.

The dataset holds records about the security of AI software: vulnerability advisories for LLM SDKs, agent frameworks, model-serving software and other AI software, together with incidents, research, policy documents and news about AI. Records are collected from public sources. A language model classifies and summarizes each record under versioned prompts, and records with a CVE are enriched from public catalogs (FIRST EPSS, CISA KEV, CAPEC, MITRE ATLAS). Every record links to its source, which remains the authority.

## This release

- **Records**: 8,260 (4,603 news, 2,876 vulnerability, 701 research, 71 regulatory, 9 incident).
- **Fields per record**: 48.
- **Publication dates**: 2014-01-24 to 2026-10-28.
- **Sources**: 75 sources contributed records to this release. The pipeline has 84 sources configured.
- **Classifier**: prompt v4 on claude-haiku-5-5 (8,260 records).
- **Summaries**: prompt v2 (8,260 records). 119 records have no summary because the source gave no usable text, and 5,978 state that the source discusses no mitigation.
- **Exploit signals**: 2,632 records carry a CVE. 2,625 of them have an EPSS score and 14 are listed in the CISA Known Exploited Vulnerabilities catalog. EPSS scores were read on 2026-10-10.
- **Affected packages**: 1,778 records state the affected packages and versions. For 1,147 of them the packages come from the GitHub Advisory Database entry for the same CVE, because the record's own source states none.
- **Scope**: 8,260 of 10,572 classified records are in scope and included. The other 2,312 were judged out of scope and are left out.
- **Formats**: CSV, JSON and JSONL, with identical content.
- **License**: CC-BY-4.0.

## Changes since version 3.0

- Every record was classified again with prompt v4 on claude-haiku-5-5, so all labels in this release come from one prompt and one model.
- The scope is narrower and stated. An advisory is included only when the affected product is AI or machine learning software, or the flaw is in an AI feature of a general product. Research is included only when it studies the security, safety, privacy, robustness or governance of AI systems. News, incidents and policy about AI are all included. Version 3.0 also admitted advisories for general software that is often deployed with AI workloads.
- Summaries and mitigations were rewritten under one summary prompt, recorded in `summary_prompt_version`.
- Severity for news, research and regulatory records is capped at medium. High and critical are kept for vulnerabilities and incidents.
- EPSS scores and CISA KEV status were read again for every record with a CVE. In version 3.0 they were read once, when a record arrived.
- `affected_packages` is filled for CVE records whose source states no package, from the GitHub Advisory Database entry for the same CVE. Version 3.0 left those records empty.
- Four columns are appended: `research_category`, `summary_prompt_version`, `epss_checked_at` and `kev_date_added`. Columns 1 to 44 keep the names, order and formatting of version 3.0.
- `issue_type_source` now reads the pipeline's own list of sources whose record type is set by rule.
- `source_category` no longer labels every source missing from its fixed table as news. Such a source takes the category of the record type set for it, so journals and advisory feeds added since version 3.0 read as academic and vulnerability_db.
- A CVSS rating of none (base score 0.0) is recorded as severity info.
- HTML entities left in source titles are decoded.

## Files

| File | Content |
|---|---|
| `aisecwatch-dataset-2026-10-10.csv` | One line per record with a header line. Lists are joined with "; ". |
| `aisecwatch-dataset-2026-10-10.json` | A document with a metadata block and a `records` array. Lists are arrays. |
| `aisecwatch-dataset-2026-10-10.jsonl` | One JSON object per line. |
| `CODEBOOK.md` | The field table below, as a separate file. |
| `SHA256SUMS.txt` | SHA-256 checksum of each file. |

## Fields

Origin says where a value comes from: the source's own feed or API, the classifier or the summarizer (language models with versioned prompts), enrichment from public catalogs, a value derived when the file is written, or the system.

| # | Column | Type | Origin | Description | Values in this release |
|---|---|---|---|---|---|
| 1 | `id` | uuid | system | Record identifier. It stays the same across releases. |  |
| 2 | `title` | text | source | Title as the source gives it, with HTML entities decoded. |  |
| 3 | `summary` | text | summarizer | Summary written from the source text alone, under the prompt named in summary_prompt_version. Empty when the source gave no usable text. |  |
| 4 | `solution` | text | summarizer | Fix or mitigation the source states. Reads "N/A -- no mitigation discussed in source." when the source states none. |  |
| 5 | `source_url` | text | source | URL of the original item. Unique per record. |  |
| 6 | `source_name` | text | source | Name of the source the record came from. |  |
| 7 | `published_at` | timestamp | source | Publication time the source gives, or the fetch time when it gives none. |  |
| 8 | `fetched_at` | timestamp | system | When the record was fetched. |  |
| 9 | `created_at` | timestamp | system | When the record was stored. |  |
| 10 | `labels` | list | classifier | One or two topic labels. | security (5,244), industry (3,787), policy (1,309), safety (1,001), research (998), privacy (376) |
| 11 | `severity` | text | classifier | Technical exploitability. The source's CVSS severity when it gives one, otherwise the classifier's rating (see severity_source). News, research and regulatory records are capped at medium. | info (4,438), medium (1,654), high (1,294), low (455), critical (419) |
| 12 | `issue_type` | text | classifier | Kind of record. Set from the source for the sources listed as overrides, otherwise by the classifier (see issue_type_source). | news (4,603), vulnerability (2,876), research (701), regulatory (71), incident (9) |
| 13 | `attack_type` | list | classifier | Up to two attack types. Empty when the record describes no attack. | other (2,463), prompt_injection (609), denial_of_service (547), supply_chain (411), data_extraction (209), jailbreak (188), model_evasion (155), pii_leakage (106), model_poisoning (74), model_theft (44), rag_poisoning (19), membership_inference (15) |
| 14 | `cve_id` | text | source | CVE identifier, when the record has one. |  |
| 15 | `cwe_ids` | list | source | CWE identifiers from the advisory. |  |
| 16 | `cvss_score` | number | source | CVSS base score from 0 to 10, when the source gives one. |  |
| 17 | `cvss_severity` | text | source | CVSS severity as the source states it. | high (1,026), medium (888), critical (347), low (183), none (1) |
| 18 | `affected_packages` | list | source | Affected packages with the vulnerable range and the first fixed version, for example "litellm@< 1.83.7 (fixed: 1.83.7)". They come from the advisory itself or, for a CVE record whose source states none, from the GitHub Advisory Database entry for the same CVE. Empty when neither states a package. |  |
| 19 | `affected_vendors` | list | classifier | Affected vendors, from a fixed list of 20 AI companies. |  |
| 20 | `affected_vendors_raw` | list | classifier | Company and product names as the classifier wrote them, not normalized. |  |
| 21 | `classifier_model` | text | system | Model that assigned the classifier fields. | claude-haiku-5-5 (8,260) |
| 22 | `classifier_prompt_version` | text | system | Version of the classifier prompt. | v4 (8,260) |
| 23 | `cvss_vector` | text | source | CVSS vector string from the source. |  |
| 24 | `attack_vector` | text | enrichment | Attack vector parsed from cvss_vector (CVSS v3.x). | network (665), local (85), adjacent (8), physical (1) |
| 25 | `attack_complexity` | text | enrichment | Attack complexity parsed from cvss_vector. | low (641), high (118) |
| 26 | `privileges_required` | text | enrichment | Privileges required, parsed from cvss_vector. | none (393), low (344), high (22) |
| 27 | `user_interaction` | text | enrichment | User interaction, parsed from cvss_vector. | none (604), required (155) |
| 28 | `exploit_maturity` | text | enrichment | Known exploitation. "active" means the CVE is in the CISA Known Exploited Vulnerabilities catalog, and "weaponized" means the catalog also records ransomware use. | unknown (2,618), active (13), weaponized (1) |
| 29 | `epss_score` | number | enrichment | FIRST EPSS probability, from 0 to 1, that the CVE is exploited in the next 30 days, as read at epss_checked_at. 0 means FIRST had not scored the CVE. |  |
| 30 | `patch_available` | boolean | source | Whether the source reports a fix. |  |
| 31 | `disclosure_date` | timestamp | source | Disclosure date the source gives, or the publication time when it gives none. |  |
| 32 | `capec_ids` | list | enrichment | CAPEC attack patterns mapped from cwe_ids with a fixed table. |  |
| 33 | `cross_ref_count` | integer | enrichment | Number of other records linked to this one through a CVE identifier. |  |
| 34 | `attack_sophistication` | text | classifier | Skill the attack needs, as the classifier judged it. | moderate (6,071), trivial (1,477), advanced (710), nation_state (2) |
| 35 | `impact_type` | list | classifier | Dimensions affected: confidentiality, integrity, availability, safety. | confidentiality (3,416), integrity (3,164), availability (1,732), safety (609) |
| 36 | `ai_component_targeted` | text | classifier | Main AI system component the record concerns. | agent (1,428), framework (1,312), api (650), plugin (581), model (514), inference (382), training_data (94), rag (92) |
| 37 | `llm_specific` | boolean | classifier | Whether the record is specific to large language models and not to AI or machine learning in general. |  |
| 38 | `classifier_confidence` | number | classifier | Confidence the classifier stated, from 0 to 1. It is not a calibrated probability. |  |
| 39 | `atlas_ids` | list | enrichment | MITRE ATLAS technique identifiers mapped from attack_type. |  |
| 40 | `priority` | integer | system | Priority of the source: 1 for vulnerability sources, 2 for research, 3 for news. | 3 (4,231), 1 (2,912), 2 (1,117) |
| 41 | `severity_source` | text | derived | "cvss" when severity is the source's CVSS severity, "llm" when the classifier rated the record. | llm (5,815), cvss (2,445) |
| 42 | `issue_type_source` | text | derived | "override" when the type is set from the source, "cve_inferred" for a vulnerability record that carries a CVE, "llm" when the classifier chose the type. | override (7,079), llm (1,170), cve_inferred (11) |
| 43 | `source_category` | text | derived | Broad category of the source, from a fixed table. A source the table does not list takes the category of the record type the pipeline sets for it, and "news" otherwise. | news (4,008), vulnerability_db (2,876), academic (684), ai_lab (395), vendor_blog (259), government (38) |
| 44 | `raw_content_length` | integer | derived | Length in characters of the source text held for the record. The text itself is not redistributed. |  |
| 45 | `research_category` | text | classifier | Kind of research record. Empty for records that are not research. | peer_reviewed (549), industry (82), preprint (62), blog (8) |
| 46 | `summary_prompt_version` | text | system | Version of the prompt that wrote summary and solution. | v2 (8,260) |
| 47 | `epss_checked_at` | timestamp | enrichment | When epss_score was last read from FIRST. |  |
| 48 | `kev_date_added` | date | enrichment | Date CISA added the CVE to its Known Exploited Vulnerabilities catalog, when it is listed. |  |

## How the data is produced

1. **Collect.** Public sources are read every six hours through their feeds and APIs: vulnerability databases, vendor advisories, research repositories and journals, standards bodies and news outlets.
2. **Deduplicate.** A record is stored once per source URL, and one record holds each CVE.
3. **Classify.** A language model assigns relevance, labels, severity, record type, attack types, affected vendors and the other classifier fields in a single call per record. The record type is set by rule for sources that publish one kind of record.
4. **Summarize.** A language model writes the summary and the mitigation from the source text alone.
5. **Enrich.** Records with a CVE receive EPSS scores from FIRST, CISA KEV status, CAPEC patterns mapped from their CWE identifiers and parsed CVSS components. Attack types are mapped to MITRE ATLAS techniques.
6. **Refresh.** EPSS scores are read again about once a day and KEV status on every cycle, with the dates recorded.

The prompts, the scope rule and the statistics of the classifier audit are published at https://aisecwatch.com/methods.

## Label reliability

The classifier fields were checked on a stratified sample of 259 classified records (up to 50 per record type, plus records judged out of scope), drawn with a fixed seed. Each sampled record was labelled again by the production model (claude-haiku-5-5) and once by a reference model (claude-sonnet-5-5), with the same prompt (v4) and input. There was no human coding, so these figures measure consistency between model runs and between two models. They do not measure accuracy against human judgment.

| Field | Statistic | Second run: n | agreement | statistic | 95% interval | Reference model: n | agreement | statistic | 95% interval |
|---|---|---|---|---|---|---|---|---|---|
| Relevant to AI security | Cohen's kappa | 259 | 98.8% | 0.96 | 0.92 to 1.00 | 259 | 94.2% | 0.82 | 0.72 to 0.90 |
| Record type | Cohen's kappa | 47 | 89.4% | 0.85 | 0.70 to 0.97 | 199 | 88.4% | 0.85 | 0.79 to 0.91 |
| Severity | weighted kappa | 162 | 98.8% | 0.99 | 0.98 to 1.00 | 199 | 93.0% | 0.97 | 0.95 to 0.99 |
| Attack sophistication | weighted kappa | 207 | 97.1% | 0.94 | 0.89 to 0.98 | 199 | 88.9% | 0.79 | 0.70 to 0.87 |
| AI component targeted | Cohen's kappa | 207 | 93.7% | 0.92 | 0.87 to 0.96 | 199 | 79.9% | 0.74 | 0.67 to 0.81 |
| LLM-specific | Cohen's kappa | 207 | 97.6% | 0.95 | 0.90 to 0.99 | 199 | 85.4% | 0.70 | 0.59 to 0.79 |
| Attack types | mean Jaccard | 207 | 95.2% | 0.95 | 0.92 to 0.98 | 199 | 76.4% | 0.81 | 0.76 to 0.86 |

The second-run columns compare the labels stored on a record with a second run of the production model. The reference columns compare that second run with the reference model. Relevance is compared on every sampled record, and the other fields on records that both sets of labels place in scope. In the second-run comparison, record type and severity count only where the model set the stored value, and not a source rule or a CVSS rating, which is why n is smaller there. For attack types, agreement is the share of records with identical sets. Intervals are percentile bootstrap intervals. The sample with all three sets of labels is at https://aisecwatch.com/methods/classifier-audit.csv.

## Limitations

- Labels and summaries are produced automatically and can be wrong. Decisions should rest on the linked source.
- Coverage follows the sources that are read. A missing record is not evidence that a problem does not exist.
- EPSS scores and KEV status are a snapshot taken on the dates above. Both change over time.
- `affected_packages` is filled for 1,778 of 2,876 vulnerability records. Of the rest, 1,047 carry a CVE and were looked up in the GitHub Advisory Database, which states no package for them, and 51 carry no CVE.
- `classifier_confidence` is the classifier's own statement and is not a calibrated probability.
- The source text is not redistributed. `raw_content_length` gives its length.

## Access

- Site: https://aisecwatch.com
- Dataset page: https://aisecwatch.com/dataset
- Methods: https://aisecwatch.com/methods
- REST API: https://aisecwatch.com/api/v1/issues (60 requests per minute, no key)
- Current export: https://aisecwatch.com/api/issues/export (CSV), `?format=json`, `?format=jsonl`
- STIX 2.1: https://aisecwatch.com/api/v1/issues/stix

## Citation

```bibtex
@misc{luu2026aisecwatch_dataset,
  author       = {Luu, T.J.},
  title        = {{AI Sec Watch Dataset}: Structured {AI} Security Threat Intelligence},
  year         = {2026},
  url          = {https://aisecwatch.com/dataset},
  note         = {48 fields per issue. Available in CSV, JSON, JSONL.}
}
```

## Author

**Truong (Jack) Luu**
Ph.D., Information Systems, University of Cincinnati. Assistant Professor, Texas State University.
- Website: https://jackluu.io
- ORCID: https://orcid.org/0000-0002-3202-3616
- Google Scholar: https://scholar.google.com/citations?user=8ifYPo0AAAAJ

## License

This dataset is released under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/).
