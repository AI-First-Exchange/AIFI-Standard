# COPYRIGHT & HUMAN AUTHORSHIP GUIDANCE
(AIFI Standard — AI First Exchange / AIFX)

This document provides **non-authoritative guidance** on documenting
declared human creative involvement in AI-assisted image workflows
using AIFX formats.

It does not constitute legal advice and does not guarantee copyright
eligibility under any jurisdiction.

---

## 1. Human Creative Contribution (General Guidance)

In many jurisdictions, copyright protection for AI-assisted images
depends on the presence of **meaningful human creative contribution**.

Such contribution may include, but is not limited to:
- Writing or refining prompts or textual descriptions
- Guiding style, composition, lighting, color, or mood
- Selecting, rejecting, or curating generated outputs
- Editing, enhancing, or refining AI-generated images
- Combining AI outputs with human-created elements

Purely autonomous image generation without human creative direction
may not qualify for copyright protection under current law.

> Interpretation of copyright eligibility is determined by applicable
> legal authorities and courts, not by AIFX.

---

## 2. How AIFI Supports Documentation

The **AI First Image Format (AIFI)** supports structured documentation
of declared human involvement through metadata, provenance records,
and workflow context.

An AIFI image may include:
- Declared creator identity (name, handle, optional contact details)
- Human-authored prompts and negative prompts
- Model identifiers and generation parameters
- Editing or post-processing notes
- Creation timestamps and provenance trail

These records are intended to support **transparency and contextual
understanding** of the creative process.

---

## 3. Optional Manifest Fields

Creators MAY include the following optional fields in `manifest.json`
to document declared human involvement:

```json
"human_authorship_statement": "",
"human_signature": "",
"creator_email": "",
"editorial_notes": "",
"human_editing_steps": [],
"human_curated_output": true
