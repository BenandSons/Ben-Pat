# Persona Pipeline

## Purpose

This file defines the recommended execution order for editor personas when improving real content. The goal is to avoid duplicated work, contradictory edits, and premature polishing.

## Core Rule

Do not run every persona blindly. Use the minimum sequence that fits the content type and business goal. Run broad strategic and structural editors before voice polish.

## Standard Order

### 0. Competitor Researcher

Use before keyword analysis when the content competes in live search and the SERP matters to the decision.

Why first:
- establishes the real competitive landscape
- prevents the team from optimizing in isolation
- helps distinguish true search competitors from internal assumptions

Produces:
- competitor set
- observable SERP patterns
- differentiation opportunities

### 1. Keyword Analyst

Use first when search visibility matters.

Why first:
- confirms the draft is aimed at a real query set
- prevents later editors from polishing a draft aimed at the wrong intent

Produces:
- keyword target
- supporting query set
- intent alignment notes
- data basis and confidence level

### 2. SEO Strategist

Run after keyword analysis when the content is intended to earn traffic, authority, or leads.

Why here:
- decides whether the piece is worth optimizing at all
- may recommend reframe, merge, or deprioritize before heavy editing work

Produces:
- keep/revise/merge/deprioritize verdict
- strategic SEO direction

### 3. Content Editor

Run once the piece is strategically worth fixing.

Why here:
- structure should be fixed before fact review and voice polish
- makes the draft coherent enough for later reviewers to judge meaningfully

Produces:
- structural edits
- rewritten sections
- section order changes

### 4. Fact Checker

Run after major structural changes.

Why here:
- avoids checking claims that may later be deleted
- catches risky assertions before authority polishing

Produces:
- verified, uncertain, and unsupported claims
- sourcing gaps
- rewrites for risky claims

### 5. E-E-A-T Reviewer

Run after factual risk has been reduced.

Why here:
- credibility work is more meaningful once the draft is structurally sound and factually safer
- strengthens trust, authority, and specificity

Produces:
- authority assessment
- credibility weaknesses
- trust-building improvements

### 6. Persona Editor

Run before any publication-style editor.

Why here:
- identifies what kind of piece the article should actually be
- prevents style editors from pushing the draft in the wrong direction

Produces:
- persona fit assessment
- editorial mode recommendation
- audience-fit adjustments

### 7. One Publication-Mode Editor

Choose only one unless there is a strong reason to combine them.

Options:
- `atlantic-editor` for essayistic, analytical, intellectually serious work
- `bi-editor` for brisk, business-readable, implication-forward work
- `hbr-editor` for strategic, executive-useful, management-oriented work

Why one only:
- these editors operate on the same layer
- running multiple style editors can produce contradictory changes

Produces:
- mode-specific rewrites
- framing and cadence improvements
- publication-fit edits

### 8. External Persona Micro-Infusion

Run after the publication-mode editor and before the final owner-voice pass.

Why here:
- structure, strategy, and factual risk should already be settled
- external personas should add light human texture, not reshape the draft
- this is the right place to add subtle depth from compatible outside voices without overriding site voice

Use:
- `/Users/chubbybebe/Documents/ChubbyBebe/Styleguides/PersonaUsage.md`
- `/Users/chubbybebe/Documents/ChubbyBebe/Styleguides/Personas/`
- `memory/workflows/external-persona-infusion.md`

Rule:
- choose only relevant personas for the audience and source material
- apply them lightly, not mechanically
- do not force every persona into every article

Produces:
- small framing upgrades
- more human explanatory texture
- subtle perspective improvements

### 9. Ben Voice Editor

Always last when the draft is meant for Ben's working standard.

Why last:
- final polish should not be overwritten by later strategic or structural editing
- this layer removes AI residue and aligns tone with Ben's preferences

Produces:
- final phrasing pass
- removal of fluff and weak transitions
- sharper, more direct prose

## Audit Mode

Use audit mode when testing the workflow itself rather than producing final copy.

Purpose:
- detect overlap between style-layer personas
- expose contradictions in editing behavior
- identify where one persona is rewriting work that should belong to another

Audit rule:
- you may run multiple style-layer editors on the same draft
- randomize the order among:
  - `atlantic-editor`
  - `bi-editor`
  - `hbr-editor`
  - `ben-voice-editor`
- record what each one tries to change
- note where edits conflict or duplicate each other

Production rule:
- do not use randomized style order for final publishing work
- in production, choose one of `atlantic-editor`, `bi-editor`, or `hbr-editor`
- keep `ben-voice-editor` last

## Skip Logic

Skip personas when they do not match the task:
- skip `keyword-analyst` and `seo-strategist` for non-search pieces
- skip `fact-checker` when the content is purely internal brainstorming with no factual claims
- skip `persona-editor` when the destination and mode are already fixed and obvious
- skip publication-mode editors for purely functional or utilitarian drafts

## Conflict Rules

- strategic verdict outranks stylistic preference
- factual corrections outrank tonal elegance
- structural clarity outranks sentence polish
- Ben voice polish should refine, not overturn, the chosen editorial mode

## Typical Sequences

### Search-Driven Site Article

1. Competitor Researcher
2. Keyword Analyst
3. SEO Strategist
4. Content Editor
5. Fact Checker
6. E-E-A-T Reviewer
7. Persona Editor
8. BI Editor or HBR Editor
9. External Persona Micro-Infusion
10. Ben Voice Editor

### Authority Essay

1. Content Editor
2. Fact Checker
3. E-E-A-T Reviewer
4. Persona Editor
5. Atlantic Editor
6. External Persona Micro-Infusion
7. Ben Voice Editor

### Practical Business Explainer

1. Competitor Researcher
2. Keyword Analyst
3. SEO Strategist
4. Content Editor
5. Fact Checker
6. Persona Editor
7. BI Editor
8. External Persona Micro-Infusion
9. Ben Voice Editor

## Output Handling

Each persona should inherit the previous revision, not restart from the original draft. Preserve the decision trail:
- what changed
- why it changed
- what remains unresolved

The goal is a staged editorial process, not ten disconnected opinions.
