# Location Page Audit Workflow

## Purpose

Audit and update a country or destination page for SwiftCargo using the live page, a dated working-copy JSON file, GSC data when available, and current SERP competitors.

## Inputs

- live URL
- country directory under `packages/sites/cargo-swift-logistics/src/app/<country>`
- dated JSON working file for the requested locale
- page-specific GSC export if available
- broader site GSC export if page data is missing
- live SERP results for the target query set

## Working File Rule

- always edit a dated duplicate, never the undated production source
- create the new working file in the same country directory before starting the audit
- for English runs, duplicate the latest `en` source into today's file
- preserve the existing schema and section structure unless explicitly told otherwise
- if today's dated file already exists, continue from that file rather than creating another duplicate

Example:

- request: `update vietnam`
- directory: `packages/sites/cargo-swift-logistics/src/app/vietnam/`
- source to copy: latest English file already in that directory
- new working file on 2026-03-17: `en.json 170326`

Translation runs can follow the same pattern later:

- request: `update vietnam fr`
- source to copy: latest `fr-FR` file already in that directory
- new working file on 2026-03-17: `fr-FR.json 170326`

## Sequence

1. Competitor Researcher
2. Keyword Analyst
3. SEO Strategist
4. Content Editor
5. Fact Checker
6. E-E-A-T Reviewer
7. Persona Editor
8. BI Editor
9. Ben Voice Editor

## Required Outputs

### 1. Competitor Audit

Store in:
- `~/.openclaw/reports/swiftcargo/locations/`

Include:
- locale-specific target queries
- at least 10 collected competitor evidence pages when the SERP allows it
- a mixed source set across official or regulatory pages, direct commercial competitors, and adjacent ranking pages
- ranking competitor pages in the target language
- competitor strengths
- competitor weaknesses
- differentiation opportunities

Do not substitute English SERP competitors for foreign-language competitors unless you explicitly label the audit as incomplete or inferred.

### 2. Page Audit

Include:
- GSC findings
- intent fit
- structural weaknesses
- trust and authority issues
- commercial fit to SwiftCargo
- prioritized fixes
- page-specific keyword horizons for 3 months, 6 months, and 12 months

### 3. Score Report

Include:
- persona-by-persona before score
- persona-by-persona after score
- net change by persona
- short explanation of why the page improved
- main remaining gaps

### 4. JSON Update

- edit only the dated JSON working file for the page
- do not overwrite older dated files unless the user explicitly wants that
- do not create a new production content file
- keep the existing JSON schema and section structure unless explicitly told otherwise

## Rules

- do not invent rankings or performance
- do not claim GSC findings that are not present in the export
- when page-level GSC is missing, label conclusions as inferred
- respect the fixed JSON structure if the implementation depends on it

## International Locale Audit Rule

- For non-English runs, audit the locale page against the latest updated English working file for structural alignment.
- Then audit the locale wording on its own merits for native readability, search competitiveness, and commercial sharpness.
- Do not pass a locale page just because it is an accurate translation.
- Call out when a locale page is structurally aligned but still weak as local-language SEO copy.

- Keywords and SERP competitors for non-English pages must be localized to the target language.
- Structural alignment to English does not remove the need for separate local keyword and competitor research.
