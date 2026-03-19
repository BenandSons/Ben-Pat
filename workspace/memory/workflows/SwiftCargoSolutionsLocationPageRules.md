# Swift Cargo Solutions — Location Page Rules

## 🧠 Core Principle

All language versions of a single **location page** (e.g., Cambodia) must share an **identical structural schema**, even if the **content, keyword targeting, and topical focus differ**.

- Structure = fixed
- Content = flexible

This rule file is used at the **final normalization stage** after the pages have already been independently improved in each language. Its purpose is not to control how earlier optimization files make decisions. Its purpose is to make the finished language files structurally compatible before handoff to developers and production.

---

## 🔒 Structural Consistency Rules

### 1. List Item Parity (Critical Rule)

All lists must contain the **same number of items across all languages**.

**Examples:**
- Ports list
- Services list
- Features list

**Conflict Handling Logic:**
When list lengths differ:
- Choose a standardized count
- Preferred approach: **match the highest count (max)**

**Example:**
- English: 3 ports  
- French: 4 ports  
- Russian: 5 ports  

👉 Final decision: All languages updated to **5 ports**

---

### 2. FAQ Count Consistency

Each location must have a **fixed number of FAQs**, identical across all languages.

**Important:**
- FAQs do **NOT need to be direct translations**
- They can be fully different in wording, search intent, keyword targeting, and topical angle
- The only requirement is that the **count matches across all languages**

**Example (Cambodia):**
- If decided: 12 FAQs  
👉 All languages must have **exactly 12 FAQs**

---

### 3. Component Count Consistency (JSON Integrity)

All structural components must match exactly across languages.

This includes:
- Number of blocks
- Component types
- Order of components

### 3.1 Section Parity (Critical Rule)

All sections (top-level content blocks) must be **identical across all language files**.

**Rule:**
- No language may contain additional or missing sections compared to others
- Section names, order, and presence must match exactly

**Conflict Handling Logic:**
When a section exists in some languages but not others:

- If only one language contains the extra section → **remove the section** to maintain parity
- If multiple languages contain the section → **add the section to all languages**

**Example:**
- Korean: includes `Support Team` and `Next Steps`
- English/French/Russian: do not include these sections

👉 Resolution (single-language case): Remove from Korean

👉 Resolution (multi-language case): Add to all languages

**Important:**
- If removing a section would result in loss of valuable content, attempt to **reintegrate that content into existing sections** without breaking structural rules

⚠️ Section parity is mandatory and takes priority over localized structural differences

---

### 4. Component Type Matching

Each component type must appear the **same number of times** across all languages.

**Example:**
Component: `type: paragraph`

- English: 1 paragraph  
- Korean: 3 paragraphs  

👉 Must resolve to either:
- Breakup/Increase English → 3 paragraphs  
- OR compress Korean → 1 paragraph

The decision is purely about structural compatibility. It is **not** about forcing the content in those paragraphs to discuss the same topic or to mirror another language version.

### 4.1 Hero Placeholder Edge Case (Required UI Fields)

The `hero.destinationPlaceholder` and `hero.departurePlaceholder` fields are **required UI schema fields** for location pages.

**Rule:**
- If one language contains these fields and others do not, **add them to the missing languages**
- Do **not** treat these placeholder fields as removable localized extras
- Keep the fields in the same position inside the `hero` object across all languages

**Reason:**
- These are interface fields, not optional content variations
- Removing them can create an incomplete search form configuration for that location

---

### 5. Text Length Flexibility

Text length and topical content do **NOT need to match**.

- English: 2 sentences about shipping speed  
- French: 8 sentences about customs support  

✅ Allowed — as long as the structural count and component layout are preserved

---

### 6. Restricted Goods — Human-Only Editing

The **"Restricted Goods"** section must be edited **by a human only**.

**Rules:**
- This section must **not be generated, modified, expanded, or normalized by automated rule files or AI processes**
- Do not alter item counts, wording, or structure in this section during normalization
- Do not attempt to reconcile differences across languages for this section

**Reason:**
- The content may contain **legal, compliance, or jurisdiction-specific requirements**
- Incorrect modification could introduce **regulatory risk or misinformation**

**Allowed Actions:**
- Preserve the section exactly as provided in each language file
- If inconsistencies exist, **flag for human review instead of modifying**

⚠️ This section is exempt from all structural normalization rules in this document

---

## ⚖️ Decision-Making Framework

When inconsistencies are found:

### Step 1: Identify the mismatch
- List length
- FAQ count
- Component count/type

### Step 2: Choose a standard

Preferred hierarchy:
1. **Max count (most complete version)**
2. **Majority count (most common)**
3. **Manual override (editor decision)**

### Step 3: Normalize all languages
- Expand or compress content to match the chosen structure

---

## 🚫 What Must NEVER Happen

- Different sections (missing or extra sections) across languages
- Different list lengths across languages  
- Different number of FAQs per language  
- Different component counts or types  
- JSON structure mismatches  

⚠️ These will break the system

---

## 🧩 What CAN Differ

- Wording  
- Language-specific phrasing  
- Topics discussed inside each matching component  
- Keyword targeting  
- FAQ questions  
- Search intent emphasis  
- Content depth / sentence count  

---

## 🏗️ Conceptual Model

> One shared JSON skeleton → Multiple localized content layers

---

## 📅 File Versioning & Date Consistency

When working with location page files, **date consistency is critical** to ensure the correct content set is being edited.

### File Naming Convention

Each language file includes a date suffix:

- `EN.json 190326`
- `FR.json 190326`
- `KR.json 190326`
- etc.

---

### Rule: Match Dates Across All Languages

All language files being edited must have the **same date**.

**Example (Valid):**
- EN.json 190326  
- FR.json 190326  
- RU.json 190326  

**Example (Invalid):**
- EN.json 190326  
- FR.json 180326 ❌

---

### Purpose

This ensures:
- You are working on the **latest version of the content set**
- You are not mixing **old and new structures**
- Structural parity rules are applied correctly

---

### Editing Guideline

When using this rule set:

- Always confirm all files share the same date before editing
- Use the latest matching-date files as the **single source of truth set**
- This rule file runs only after all other page-improvement rule files have already completed their work
- Do not force earlier optimization decisions to conform during generation; normalize only at the end
- Perform structural normalization ("linting") across this final set only

---

## 🧰 Role of This Rule File

This file is not an upstream content strategy file.

It does **not** decide how the individual language pages should be optimized while they are being improved.

By the time this rule file is used:
- The previous JSON has already been cloned
- Each language version has already been improved independently
- Memory files already define keyword goals and competitor context per language
- Multiple other rule files may already have applied language-specific improvements

This file exists only to:
- Check structural compatibility across languages
- Resolve count mismatches
- Standardize the final JSON layout
- Prevent production-breaking schema inconsistencies before developer handoff

---

## ✅ Summary

To maintain system stability:

- Structure must always match across languages
- Content, topic focus, and keyword targeting can vary freely within that structure
- File versions must align via matching dates
- This rule file is a final-stage structural normalization layer before developer handoff

Failure to follow these rules may result in **system-breaking inconsistencies**
