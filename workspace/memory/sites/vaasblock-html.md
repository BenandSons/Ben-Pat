# VaaSBlock HTML Rules

## Purpose

These rules define how raw HTML articles for `vaasblock.com` should be structured and spaced before publication.

Use this file when:
- creating a new VaaSBlock HTML article
- substantially editing an existing VaaSBlock HTML article
- cleaning formatting before handoff or publication

This file is about HTML presentation and consistency, not thesis, SEO strategy, or factual review.

## Core Principle

VaaSBlock articles should feel visually breathable, deliberate, and publication-ready inside the site’s existing WordPress styling.

The main failure to avoid is cramped section transitions where headings sit too close to preceding text.

## Heading Spacing Rule

All heading tags must have a spacer paragraph immediately before them:

```html
<p>&nbsp;</p>
<h2><b>Section Heading</b></h2>
```

Apply this to:
- `<h2>`
- `<h3>`
- `<h4>`

Do not skip this rule unless one of these is already directly above the heading:
- `<p>&nbsp;</p>`
- `<hr />`
- a wrapper block that already creates clear vertical separation

If in doubt, add the spacer.

## Default Heading Patterns

Preferred section headings:

```html
<p>&nbsp;</p>
<h2><b>Primary Section</b></h2>
```

Preferred subsection headings:

```html
<p>&nbsp;</p>
<h3><b>Subsection</b></h3>
```

Preferred minor subheads:

```html
<p>&nbsp;</p>
<h4><b>Small Subhead:</b></h4>
```

## Paragraph Spacing Rules

- Use `<p>&nbsp;</p>` to create breathing room between major blocks.
- Use one spacer only. Do not stack multiple blank paragraphs.
- After long intro blocks, TL;DR blocks, images, tables, or list-heavy sections, add a spacer before the next heading.
- Do not insert unnecessary blank paragraphs between tightly related body paragraphs.

## Intro and Opening Block

Typical opening sequence:

```html
<p><img ... /></p>

<p><em>Opening deck or framing line.</em></p>

<p>Main intro paragraph...</p>
<p>Main intro paragraph...</p>

<p>&nbsp;</p>
<h2><b>First Main Section</b></h2>
```

Do not start the page with an empty spacer before the first visual block.

## Lists

- Lists should follow a short lead-in sentence.
- Add a spacer after long lists before the next heading.
- Avoid placing a heading immediately after `</ul>` or `</ol>` without `<p>&nbsp;</p>`.

Example:

```html
</ul>
<p>&nbsp;</p>
<h2><b>Next Section</b></h2>
```

## Images

- Wrap standalone images in paragraph tags:

```html
<p><img ... /></p>
```

- If an image is followed by a new section, add a spacer before the heading unless a caption/blockquote already creates enough space.

## Tables

- Add a spacer before tables when transitioning from prose into comparison content.
- Add a spacer after tables before the next heading.

Preferred transition:

```html
<p>&nbsp;</p>
<h2><b>Comparison</b></h2>
<table>...</table>
<p>&nbsp;</p>
<h2><b>Next Section</b></h2>
```

## Blockquotes and Emphasis Blocks

- If a blockquote introduces a new thought, follow it with normal paragraphs.
- If a heading comes after a blockquote, insert `<p>&nbsp;</p>` first.

## Metadata and Schema

For new standalone authority articles, prefer:
- HTML comment block with slug and meta fields at the top
- JSON-LD near the top of the file

This metadata block should stay above the article body.

## Links

- Internal links should behave like citations, not promotions.
- External links should be added only when they improve evidence, attribution, or commercial requirements.
- Do not overload one paragraph with multiple links unless the sentence is explicitly comparative.

## End Matter

Common closing order:
- conclusion
- About VaaSBlock or author section
- disclosure or AI note if used
- sources line or sources section

If a heading appears in the end matter, it still needs the spacer rule.

## Cleanup Checklist

Before finalizing a VaaSBlock HTML page, check:
- every `<h2>`, `<h3>`, and `<h4>` has adequate spacing above it
- no heading is jammed directly against a paragraph, list, table, or image
- blank paragraphs are used intentionally, not stacked randomly
- section transitions feel consistent across the full article
- metadata stays at the top and sources stay at the bottom

## Validation Script

Use the VaaSBlock-specific checker before finalizing or handing off a page:

```bash
python3 /Users/chubbybebe/Documents/AI-content/vaasblock_html_check.py /absolute/path/to/article.html
```

Current checks include:
- missing spacer before `<h2>`, `<h3>`, or `<h4>`
- heading immediately after `</ul>`, `</ol>`, or `</table>` without a spacer
- missing metadata comment block near the top of the file
- missing JSON-LD near the top of the file
- overly dense paragraphs containing more than two links

Use the script as a formatter-sanity check, not as a replacement for editorial judgment.

## Safe Default

If you are editing quickly and unsure about spacing, use this default:

```html
<p>&nbsp;</p>
<h2><b>Heading</b></h2>
```

For VaaSBlock HTML, slightly too much breathing room is usually better than cramped transitions.
