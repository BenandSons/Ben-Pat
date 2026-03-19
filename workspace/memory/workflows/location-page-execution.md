# SwiftCargo Location Page Execution Workflow

## Purpose

Handle end-to-end SwiftCargo location page updates from a short request like `update vietnam`.

This workflow turns the audit process into a production routine:
- create today's dated working file
- analyze the live page and the current source
- run the persona sequence
- update the dated JSON
- save the audit artifacts

## Trigger Format

Supported request shapes:

- `update vietnam`
- `update singapore`
- `update cambodia`

Translation mode can be added with the same pattern:

- `update vietnam fr`
- `update singapore it`

## Date Format

Use `DDMMYY` for new working files.

Example:

- 2026-03-17 -> `170326`

## File Creation Rule

For any requested country:

1. open `packages/sites/cargo-swift-logistics/src/app/<country>/`
2. identify the latest file for the requested locale already in that directory
3. duplicate that file into a new working file stamped with today's date
4. edit only the new dated file for the rest of the run

## Locale Rules

### English Default

If the request is `update vietnam`, assume English.

- source pattern: latest `en` file in the directory
- new working file pattern: `en.json <DDMMYY>` when that naming convention is already used in the directory

### Translation Later

If the request includes a locale, use that locale's latest file as the source.

Examples:

- `fr` -> latest `fr-FR` file
- `it` -> latest `it-IT` file
- `ru` -> latest `ru-RU` file
- `kr` -> latest `kr-KR` file

Create the dated duplicate first. Translation-specific editing logic can be layered later.

## Execution Steps

1. Resolve country and locale from the request.
2. Open the country directory.
3. Find the latest matching locale file.
4. Create today's dated working copy in the same directory.
5. Read the live page and current working source.
6. Gather GSC data if available. If page-level data is missing, label findings as inferred.
7. Run locale-specific competitor and keyword research in the target language. Do not reuse the English competitor or keyword set as a substitute for local SERP evidence.
8. Collect at least 10 competitor evidence pages when the SERP allows it, using a mixed source set:
   - official or regulatory pages when they shape customs, tax, inspection, or compliance logic
   - direct mover or removalist competitor pages
   - adjacent commercial or editorial pages that rank for the same intent
9. Run the SwiftCargo location-page persona sequence:
   - Competitor Researcher
   - Keyword Analyst
   - SEO Strategist
   - Content Editor
   - Fact Checker
   - E-E-A-T Reviewer
   - Persona Editor
   - BI Editor
   - Ben Voice Editor
10. Update the dated JSON while preserving the schema.
11. Save the audit report to `~/.openclaw/reports/swiftcargo/locations/`.
12. Save a before/after score report for every run.
13. Save page-specific keyword horizons in the report MD:
   - 3-month keyword targets
   - 6-month keyword targets
   - 12-month keyword targets
14. Report back with:
   - the file created
   - the file edited
   - the main changes made
   - whether GSC conclusions were validated or inferred

## Output Expectations

Every run should leave:

- one new dated working file in the country directory
- one audit report in `~/.openclaw/reports/swiftcargo/locations/`
- one page-specific keyword horizon block in that audit report covering 3 months, 6 months, and 12 months
- one before/after score report

## Guardrails

- do not edit `page.tsx` unless the task explicitly requires code changes
- do not rewrite the JSON schema
- do not silently edit an older dated file when today's working file should be created
- do not invent GSC or SERP findings
- do not treat translation mode as simple machine replacement if factual or locale-specific adaptation is required

## Notes From Singapore

The Singapore run confirmed the right default pattern:

- duplicate the locale JSON in the same directory first
- preserve structure
- use the new dated file as the working copy
- keep audit conclusions explicit about what is inferred versus validated

## International Localization Rules

- For locale runs, use the latest updated English page for that country as the structural model.
- Preserve section order, conversion logic, and factual claims unless a locale-specific adaptation is required.
- Do not treat locale work as literal translation. Rewrite headings, metadata, CTAs, and body sections as needed for native-language competitiveness.
- Judge success by whether the page could compete against native-language search results, not by closeness to English wording.
- See `memory/workflows/international-localization-rules.md` for the full rule set.

- Use separate competitors and keywords for each locale.
- English pages define structure; locale SERPs define search competition.
