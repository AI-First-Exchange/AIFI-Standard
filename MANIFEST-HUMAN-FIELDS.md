# OPTIONAL MANIFEST FIELDS FOR HUMAN AUTHORSHIP DOCUMENTATION
(AIFI Standard — AI First Exchange / AIFX)

The following optional fields MAY be included in an AIFI `manifest.json`
to document **declared human involvement** in AI-first image workflows.

These fields are intended to support transparency, attribution,
and contextual authorship documentation. They do not assert
legal conclusions outside the recorded creation process.

## Optional Fields

```json
"human_authorship_statement": "",
"human_signature": "",
"creator_email": "",
"editorial_notes": "",
"human_editing_steps": [],
"human_curated_output": true
```
Field Descriptions

human_authorship_statement
A creator-provided declaration describing human creative involvement
(e.g., prompt design, selection, editing, or curation).

human_signature
A non-cryptographic or cryptographic signature associated with the
authorship statement (implementation-dependent).

creator_email
Optional contact information for the declaring creator.

editorial_notes
Free-form notes describing human creative decisions, refinements,
or aesthetic direction applied to the image.

human_editing_steps
Optional array documenting post-generation edits, adjustments,
or curation steps performed by a human.

human_curated_output
Boolean flag indicating that the final image output was selected,
refined, or curated by a human.

Notes

All fields are optional

Fields are declarative, not forensic

Interpretation of these fields is the responsibility of downstream
platforms, legal systems, or rights holders
